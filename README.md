<ol>
<li><p>Compile e inicie a API Web executando o seguinte comando:</p>
<pre><code class="lang-dotnetcli">dotnet run
</code></pre>
</li>
<li><p>Abra novamente o terminal <code>httprepl</code> existente ou um novo terminal integrado do Visual Studio Code selecionando <strong>Terminal</strong>&gt;<strong>Novo Terminal</strong> no menu principal.</p>
</li>
<li><p>Se você abriu um novo terminal, conecte-se à API Web executando o seguinte comando:</p>
<pre><code class="lang-dotnetcli">httprepl https://localhost:{PORT}
</code></pre>
<p>Outra opção é executar o seguinte comando a qualquer momento enquanto <code>HttpRepl</code> estiver em execução:</p>
<pre><code class="lang-dotnetcli">connect https://localhost:{PORT}
</code></pre>
</li>
<li><p>Vá até o ponto de extremidade <code>Pizza</code> executando o seguinte comando:</p>
<pre><code class="lang-dotnetcli">cd Pizza
</code></pre>
</li>
<li><p>Execute o seguinte comando para ver as novas ações na API de Pizza:</p>
<pre><code class="lang-dotnetcli">ls
</code></pre>
<p>O comando anterior mostra uma saída das APIs disponíveis para o ponto de extremidade <code>Pizza</code>:</p>
<pre><code class="lang-output">    https://localhost:{PORT}/Pizza&gt; ls
    .      [GET|POST]
    ..     []
    {id}   [GET|PUT|DELETE]
</code></pre>
</li>
<li><p>Faça uma solicitação <code>POST</code> para adicionar uma nova pizza a <code>HttpRepl</code> usando o seguinte comando:</p>
<pre><code class="lang-dotnetcli">post -c &quot;{&quot;name&quot;:&quot;Hawaii&quot;, &quot;isGlutenFree&quot;:false}&quot;
</code></pre>
<p>O comando anterior retorna uma lista de todas as pizzas:</p>
<pre><code class="lang-output">HTTP/1.1 201 Created
Content-Type: application/json; charset=utf-8
Date: Fri, 02 Apr 2021 23:23:09 GMT
Location: https://localhost:{PORT}/Pizza?id=3
Server: Kestrel
Transfer-Encoding: chunked

{
    &quot;id&quot;: 3,
    &quot;name&quot;: &quot;Hawaii&quot;,
    &quot;isGlutenFree&quot;: false
}
</code></pre>
</li>
<li><p>Atualize a nova pizza <code>Hawaii</code> para uma pizza <code>Hawaiian</code> com uma solicitação <code>PUT</code> usando o seguinte comando:</p>
<pre><code class="lang-dotnetcli">put 3 -c  &quot;{&quot;id&quot;: 3, &quot;name&quot;:&quot;Hawaiian&quot;, &quot;isGlutenFree&quot;:false}&quot;
</code></pre>
<p>O comando anterior retorna a seguinte saída que indica êxito:</p>
<pre><code class="lang-output">HTTP/1.1 204 No Content
Date: Fri, 02 Apr 2021 23:23:55 GMT
Server: Kestrel
</code></pre>
<p>Para verificar se a pizza foi atualizada, execute novamente a ação <code>GET</code> usando o seguinte comando:</p>
<pre><code class="lang-dotnetcli">get 3
</code></pre>
<p>O comando anterior retorna a pizza recém-atualizada:</p>
<pre><code class="lang-output">HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Date: Fri, 02 Apr 2021 23:27:37 GMT
Server: Kestrel
Transfer-Encoding: chunked

{
    &quot;id&quot;: 3,
    &quot;name&quot;: &quot;Hawaiian&quot;,
    &quot;isGlutenFree&quot;: false
}
</code></pre>
</li>
<li><p>Nossa API também pode excluir a pizza recém-criada por meio da ação <code>DELETE</code> se você executar o seguinte comando:</p>
<pre><code class="lang-dotnetcli">delete 3
</code></pre>
<p>O comando anterior retorna um resultado <code>204 No Content</code> para êxito:</p>
<pre><code class="lang-output">HTTP/1.1 204 No Content
Date: Fri, 02 Apr 2021 23:30:04 GMT
Server: Kestrel
</code></pre>
<p>Para verificar se a pizza foi removida, execute novamente a ação <code>GET</code> usando o seguinte comando:</p>
<pre><code class="lang-dotnetcli">get
</code></pre>
<p>O comando anterior retorna as pizzas originais como resultados:</p>
<pre><code class="lang-output">HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Date: Fri, 02 Apr 2021 23:31:15 GMT
Server: Kestrel
Transfer-Encoding: chunked

[
    {
        &quot;id&quot;: 1,
        &quot;name&quot;: &quot;Classic Italian&quot;,
        &quot;isGlutenFree&quot;: false
    },
    {
        &quot;id&quot;: 2,
        &quot;name&quot;: &quot;Veggie&quot;,
        &quot;isGlutenFree&quot;: true
    }
]
</code></pre>
</li>
</ol>
