{% highlight java %}
public class NioEchoClient {

    private String ip;
    private int port;

    public NioEchoClient(String ip, int port) {
        this.ip = ip;
        this.port = port;
    }

    public void start() throws IOException {
        IoConnector connector = NioFactory.newTcpConnectorBuilder(new NioEchoClientHandler())
                                          .connectTimeoutInMillis(3000).build();
        connector.connect(ip, port);
    }

    public static void main(String[] args) throws IOException {
        new NioEchoClient("127.0.0.1", 1314).start();
    }
}
{% endhighlight %}
