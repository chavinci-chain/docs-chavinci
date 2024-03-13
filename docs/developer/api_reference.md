# __API reference (JSON-RPC)__

## __Controlling Chavinci Core__
Run chad -server. You can control it via the command-line cha-cli utility or by HTTP JSON-RPC commands.

You must create a chachain.conf configuration file setting an rpcuser and rpcpassword; see <ins style="text-decoration:underline;text-decoration-color: #526cfe;">[Running Chavinci](/developer/node/node/)</ins> for details.


Now run:
```shell
$ ./chad -daemon
    ChaChain server starting
$ ./cha-cli -rpcwait help
    # shows the help text
```

A <ins style="text-decoration:underline;text-decoration-color: #526cfe;">[list of RPC calls](/developer/rpc/)</ins>  will be shown.

```shell
$ ./cha-cli getbalance
 2000.00000
```

## __Languages__

### Python

While ChavinciRPC lacks a few obscure features from jsonrpc, software using only the ServiceProxy class can be written the same to work with either version the user might choose to install:

```python
from jsonrpc import ServiceProxy
  
access = ServiceProxy("http://user:password@127.0.0.1:8332")
access.getblockchaininfo()
access.listreceivedbyaddress(6)
#access.sendtoaddress("c7669qi6uJio8xF9qfhoWNTroghgXkm5yA", 10)
```

### Ruby

```ruby
require 'net/http'
require 'uri'
require 'json'

class ChavinciRPC
  def initialize(service_url)
    @uri = URI.parse(service_url)
  end

  def method_missing(name, *args)
    post_body = { 'method' => name, 'params' => args, 'id' => 'jsonrpc' }.to_json
    resp = JSON.parse( http_post_request(post_body) )
    raise JSONRPCError, resp['error'] if resp['error']
    resp['result']
  end

  def http_post_request(post_body)
    http    = Net::HTTP.new(@uri.host, @uri.port)
    request = Net::HTTP::Post.new(@uri.request_uri)
    request.basic_auth @uri.user, @uri.password
    request.content_type = 'application/json'
    request.body = post_body
    http.request(request).body
  end

  class JSONRPCError < RuntimeError; end
end

if $0 == __FILE__
  h = ChavinciRPC.new('http://user:password@127.0.0.1:8332')
  p h.getbalance
  p h.getblockchaininfo
  p h.getnewaddress
  p h.dumpprivkey( h.getnewaddress )
end
```


### PHP
The JSON-RPC PHP library also makes it very easy to connect to Chavinci. For example:
```php
  require_once 'jsonRPCClient.php';
  
  $chavinci = new jsonRPCClient('http://user:password@127.0.0.1:8332/');
   
  echo "<pre>\n";
  print_r($chavinci->getblockchaininfo()); echo "\n";
  echo "Received: ".$chavinci->getreceivedbylabel("Your Address")."\n";
  echo "</pre>";
```

### Java

The easiest way to tell Java to use HTTP Basic authentication is to set a default Authenticator:

```java 
final String rpcuser ="...";
final String rpcpassword ="...";
  
Authenticator.setDefault(new Authenticator() {
    protected PasswordAuthentication getPasswordAuthentication() {
        return new PasswordAuthentication (rpcuser, rpcpassword.toCharArray());
    }
});
```

### Perl
The JSON::RPC package from CPAN can be used to communicate with Chavinci. You must set the client's credentials; for example:

```perl
use JSON::RPC::Client;
use Data::Dumper;

my $client = new JSON::RPC::Client;

$client->ua->credentials(
    'localhost:8332', 'jsonrpc', 'user' => 'password'  # REPLACE WITH YOUR chachain.conf rpcuser/rpcpassword
    );

my $uri = 'http://localhost:8332/';
my $obj = {
    method  => 'getblockchaininfo',
    params  => [],
};

my $res = $client->call( $uri, $obj );

if ($res){
    if ($res->is_error) { print "Error : ", $res->error_message; }
    else { print Dumper($res->result); }
} else {
    print $client->status_line;
}
```


### .NET (C#)

The communication with the RPC service can be achieved using the standard http request/response objects. A library for serializing and deserializing Json will make your life a lot easier:

Json.NET ( http://james.newtonking.com/json ) is a high performance JSON package for .NET. It is also available via NuGet from the package manager console ( Install-Package Newtonsoft.Json ).

The following example uses Json.NET:

```
 HttpWebRequest webRequest = (HttpWebRequest)WebRequest.Create("http://localhost.:8332");
 webRequest.Credentials = new NetworkCredential("user", "pwd");
 /// important, otherwise the service can't desirialse your request properly
 webRequest.ContentType = "application/json-rpc";
 webRequest.Method = "POST";
  
 JObject joe = new JObject();
 joe.Add(new JProperty("jsonrpc", "1.0"));
 joe.Add(new JProperty("id", "1"));
 joe.Add(new JProperty("method", Method));
 // params is a collection values which the method requires..
 if (Params.Keys.Count == 0)
 {
  joe.Add(new JProperty("params", new JArray()));
 }
 else
 {
     JArray props = new JArray();
     // add the props in the reverse order!
     for (int i = Params.Keys.Count - 1; i >= 0; i--)
     {
        .... // add the params
     }
     joe.Add(new JProperty("params", props));
     }
  
     // serialize json for the request
     string s = JsonConvert.SerializeObject(joe);
     byte[] byteArray = Encoding.UTF8.GetBytes(s);
     webRequest.ContentLength = byteArray.Length;
     Stream dataStream = webRequest.GetRequestStream();
     dataStream.Write(byteArray, 0, byteArray.Length);
     dataStream.Close();
     
     
     WebResponse webResponse = webRequest.GetResponse();
     
     ... // deserialze the response
```

### NodeJS

Example using chavinci-core:

```
const Client = require('chavinci-core');
const client = new Client({ 
  network: 'regtest', 
  username: 'user', 
  password: 'pass', 
  port: 18443 
});

client.getBlockchainInfo().then((help) => console.log(help));
```

### Command line (cURL)
You can also send commands and see results using cURL or some other command-line HTTP-fetching utility; for example:
```
curl --user user --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "getblockchaininfo", "params": [] }' 
-H 'content-type: text/plain;' http://127.0.0.1:8332/
```
You will be prompted for your rpcpassword, and then will see something like:
```
{"result":{"balance":0.000000000000000,"blocks":59952,"connections":48,"proxy":"","generate":false,
    "genproclimit":-1,"difficulty":16.61907875185736},"error":null,"id":"curltest"}
```

### Command line (jsonrpc-cli)

<ins style="text-decoration:underline;text-decoration-color: #526cfe;">[jsonrpc-cli](https://github.com/dan-da/jsonrpc-cli)</ins> provides simple json queries from the command-line with highlighted json results (colors) and the ability to view/debug raw http requests and responses.

```
 jsonrpc-cli --user=rpcuser --pass=rpcpassword  http://localhost:8332/ getblockchaininfo
```