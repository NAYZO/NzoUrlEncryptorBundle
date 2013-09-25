<h1>NzoUrlEncryptorBundle</h1>

<p>The <strong>UrlEncryptorBundle</strong> is a Symfony2 Bundle used to Encrypt and Decrypt the variables in url and links and to provide more security in term of access to your project.</p>

<h1>Documentation</h1>

<h3>Getting Started With NzoUrlEncryptorBundle</h3>

<p>The <strong>UrlEncryptorBundle</strong> is easy to install, it contain a global configuration option to make the use more easier.</p>

<h4>Installation via Composer</h4>

<pre><span class="p">{</span>
    <span class="s2">"require"</span><span class="o">:</span> <span class="p">{</span>
        <span class="s2">"nzo/url-encryptor-bundle"</span><span class="o">:</span> <span class="s2">"dev-master"</span>
    <span class="p">}</span>
<span class="p">}</span>
</pre>
 
<h4>Enable the bundle</h4>
<p> Enable the bundle in the kernel:</p>

<pre><span class="o">&lt;?</span><span class="nx">php</span>
<span class="c1">// app/AppKernel.php</span>

<span class="k">public</span> <span class="k">function</span> <span class="nf">registerBundles</span><span class="p">()</span>
<span class="p">{</span>
    <span class="nv">$bundles</span> <span class="o">=</span> <span class="k">array</span><span class="p">(</span>
        <span class="c1">// ...</span>
        <span class="k">new</span> <span class="nx">Nzo\UrlEncryptorBundle\NzoUrlEncryptorBundle</span><span class="p">(),</span>
    <span class="p">);</span>
<span class="p">}</span>
</pre>

<h4>Configure your application's config.yml</h4>
<p>The secure value in the configuration must contain a random key string of maximum 8 caracters and minimum of one caracter.</p>

<pre><span class="c1"># app/config/config.yml</span>
<span class="l-Scalar-Plain">nzo_url_encryptor</span><span class="p-Indicator">:</span>
    <span class="l-Scalar-Plain">secret</span><span class="p-Indicator">:</span> <span class="l-Scalar-Plain">YourSecretEncryptionKey</span> 
</pre>

<h4>Use in Twig template</h4>

<pre>
// use to encrypt the id in the url

<a href="{{path('my-path-in-the-routing', {'id': MyId | urlencrypt } )}}"> Click me </a>

</pre>

<h4>Use in Controller</h4>

<pre>
// use to decrypt the encrypted 'Id' comming from the routing

    public function indexAction($encrypted_id) 
    {
        $Id = $this->get('nzo_url_encryptor')->decrypt($encrypted_id);

        //....
    }    
</pre>

<h4>Note</h4>

<p>the 