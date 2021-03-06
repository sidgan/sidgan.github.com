---
layout: post
title: "Hadoop Installation"
description: ""
category: [technical]
tags: [hadoop, big data, installation, terminal]
---
{% include JB/setup %}

<h2>Requirements:</h2> 

<h3>Java</h3>

See installation of the latest version [here](http://openjdk.java.net/install/)

<h3> A dedicated Hadoop user</h3>
 
Add a new Hadoop user and group that will access all the Hadoop files. This is the user in whose directory Hadoop will be installed and will communicate via SSH to the local user.
 
<p>
<code>
sudo addgroup hadoop
</code>
</p>
<p>
<code>
sudo adduser --ingroup hadoop hduser
</code>
</p>

<h4> Chaos </h4>

In my first Hadoop installation, I did not create a separate Hadoop user and only then could I understand why the existence of a separate user was necessary. Creating a separate user helps tremendously in terms of file permissions, security and backups. 

I did not have a separate user and so with my first execution run on Hadoop, my normal user suffered. All my file permissions changed and on booting I was only able to log into my normal account and thereafter I could not do anything. The only screen I could see was my desktop, but it was barren. All the files, disks, profile settings, directories were no where to be seen. I could not even access the terminal. The on-screen buttons like unity, network, battery, time and date settings appeared disabled. 
 
My, just a moment ago, perfectly configured laptop (or so I thought) was rendered unusable. I do not know the exact cause of this, but the only place where I deviated from the [Installation Manual](http://hadoop.apache.org/docs/stable/hadoop-project-dist/hadoop-common/SingleCluster.html) was not creating a serparate user and that is why I emphasise on creating one. 

<h4> Terminal is king </h4>

The terminal <strong>ALWAYS</strong> comes to the rescue. Thats why I love Linux so much. No matter how badly you think you have screwed up and the only possible way out now is a fresh installation (which too comes free. :D) the terminal always provides a solution. I cannot stress on the utmost importance and utility of the terminal even if I were to talk about it every single day. 

So, here is what I did. I opened my Terminal using Ctrl+Alt+F7. I checked my profile setting, and using <code>ls</code> I could see that sure enough my files were still present in my computer, but I could not view them. I figured out the problem. All the files and settings that were of my normal user had been shifted from my home directory into <code>/</code>, hence one up the directory hierarchy. I do not know why this happened. I could see the <code>sidgan</code> folder, which is my normal user within my <code>home</code> and sure enough it was completely empty. From here on, the solution seemed trivial, all I had to do was to move the entire directory structure one level down. This, I did by one simple command: 

<p>
<code>
mv source dest
</code> 
</p>

I breathed a sigh of relief and could see my splendid laptop back to its normal state with all its configuration files intact. 

<h3> SSH </h3> 

In order to access the different nodes, Hadoop uses SSH. All this is done while being logged into the <code>hduser</code> account.
Simply [generate SSH key](http://sidgan.github.io/technical/2014/09/23/generate ssh keys/) for <code>hduser</code>. 

One important thing to keep in mind is to not enter any password for the <code>hduser</code> because all the while Hadoop interacts with the nodes, the user will have to input the password each time. This is not possible, so, it is a better idea to not keep any password in the first place. 

After generating SSH key for <code>hduser</code> the next step is to enable access to the machine, ie the normal user, in my case <code>sidgan</code>. 

Test the SSH setup once by establishing a connection between the normal user and <code>hduser</code> by: 

<code>
ssh localhost
</code>

<h3> IPv6 and IPv4 </h3>

Disable IPv6 only for Hadoop by adding the given line to <code> conf/hadoop-env.sh </code>:
<p>
<code>
export HADOOP_OPTS=-Djava.net.preferIPv4Stack=true
</code>
</p>

<h2> Installation </h2> 
[Download Hadoop](http://www.apache.org/dyn/closer.cgi/hadoop/core) and extract its contents.
<p>
<code>
tar -xzf hadoop-1.0.3.tar.gz
</code>
<p>
It should be placed in the <code>hduser</code> directory. 
</p>
</p>

Change the owner of all files to <code>hduser</code> user and <code>hadoop</code> group. 
<p>
<code>
sudo chown -R hduser:hadoop hadoop-1.0.3
</code>
</p>


<h2> Configuration </h2>

<h3> Step 1: Update <code>.bashrc</code> file </h3>

Since the <code>hduser</code> user will be accessing the Hadoop installation, it makes sense to update the <code>.bashrc</code> file of <code>hduser</code>. The following lines as suggested in the [Installation Manual](http://hadoop.apache.org/docs/stable/hadoop-project-dist/hadoop-common/SingleCluster.html) have to be appended at the end of the <code>.bashrc</code> file. 


<h3> Step 2: Update environment variables </h3>

The <code>JAVA_HOME</code> path must be changed to the Sun JDK or JRE directory 

<p>
<code>
export JAVA_HOME=/usr/lib/jvm/java-7-sun
</code>
<p>
This is done for the <code>hduser</code>.
</p>
</p>

<h3> Step 3: HDFS </h3>

Hadoop Dedicated File System (HDFS) is the directory where Hadoop stores all the data. 

<h3> Step 4: Update <code> hadoop-env.sh </code> </h3>

Uncomment the line <code> export JAVA_HOME=/usr/lib/jvm/java-X-sun </code>, where <code> X </code> is the version number. 

<h3> Step 4: Update <code> conf/core-site.xml </code> </h3>

Add the following lines within the <code> configuration </code>  tags. 

<div class="bogus-wrapper"><notextile><figure class="code">
</pre></td><td class="code"><pre><code class="xml"><span class="line"><span class="nt">&lt;property&gt;</span>
</span><span class="line">  <span class="nt">&lt;name&gt;</span>hadoop.tmp.dir<span class="nt">&lt;/name&gt;</span>
</span><span class="line">  <span class="nt">&lt;value&gt;</span>/app/hadoop/tmp<span class="nt">&lt;/value&gt;</span>
</span><span class="line">  <span class="nt">&lt;description&gt;</span>A base for other temporary directories.<span class="nt">&lt;/description&gt;</span>
</span><span class="line"><span class="nt">&lt;/property&gt;</span>
</span><span class="line">
</span><span class="line"><span class="nt">&lt;property&gt;</span>
</span><span class="line">  <span class="nt">&lt;name&gt;</span>fs.default.name<span class="nt">&lt;/name&gt;</span>
</span><span class="line">  <span class="nt">&lt;value&gt;</span>hdfs://localhost:54310<span class="nt">&lt;/value&gt;</span>
</span><span class="line">  <span class="nt">&lt;description&gt;</span>The name of the default file system.  A URI whose
</span><span class="line">  scheme and authority determine the FileSystem implementation.  The
</span><span class="line">  uri&#39;s scheme determines the config property (fs.SCHEME.impl) naming
</span><span class="line">  the FileSystem implementation class.  The uri&#39;s authority is used to
</span><span class="line">  determine the host, port, etc. for a filesystem.<span class="nt">&lt;/description&gt;</span>
</span><span class="line"><span class="nt">&lt;/property&gt;</span>
</span></code></pre></td></tr></table></div></figure></notextile></div>


<h3> Step 4: Update <code> conf/mapred-site.xml </code> </h3>

Add the following lines within the <code> configuration </code> tags.

<div class="bogus-wrapper"><notextile><figure class="code">
</pre></td><td class="code"><pre><code class="xml"><span class="line"><span class="nt">&lt;property&gt;</span>
</span><span class="line">  <span class="nt">&lt;name&gt;</span>mapred.job.tracker<span class="nt">&lt;/name&gt;</span>
</span><span class="line">  <span class="nt">&lt;value&gt;</span>localhost:54311<span class="nt">&lt;/value&gt;</span>
</span><span class="line">  <span class="nt">&lt;description&gt;</span>The host and port that the MapReduce job tracker runs
</span><span class="line">  at.  If &quot;local&quot;, then jobs are run in-process as a single map
</span><span class="line">  and reduce task.
</span><span class="line">  <span class="nt">&lt;/description&gt;</span>
</span><span class="line"><span class="nt">&lt;/property&gt;</span>
</span></code></pre></td></tr></table></div></figure></notextile></div>


<h3> Step 4: Update <code> conf/hdfs-site.xml </code> </h3>

Add the following lines within the <code> configuration </code> tags. 

<div class="bogus-wrapper"><notextile><figure class="code">
</pre></td><td class="code"><pre><code class="xml"><span class="line"><span class="nt">&lt;property&gt;</span>
</span><span class="line">  <span class="nt">&lt;name&gt;</span>dfs.replication<span class="nt">&lt;/name&gt;</span>
</span><span class="line">  <span class="nt">&lt;value&gt;</span>1<span class="nt">&lt;/value&gt;</span>
</span><span class="line">  <span class="nt">&lt;description&gt;</span>Default block replication.
</span><span class="line">  The actual number of replications can be specified when the file is created.
</span><span class="line">  The default is used if replication is not specified in create time.
</span><span class="line">  <span class="nt">&lt;/description&gt;</span>
</span><span class="line"><span class="nt">&lt;/property&gt;</span>
</span></code></pre></td></tr></table></div></figure></notextile></div>

<h2> Start Hadoop</h2>

Run the following commands as the hadoop user, <code>hduser</code>: 

<p>
<code>
/usr/local/hadoop/bin/hadoop namenode -format
</code>
</p>

<p>
<code>
/usr/local/hadoop/bin/start-all.sh
</code>
</p>

<br/>
<img src ="/images/starting_hadoop.png" style="width:600px;height=500px">

<h2> Stop Hadoop</h2>

Run the following commands as the hadoop user, <code>hduser</code>: 

<p>
<code>
 /usr/local/hadoop/bin/stop-all.sh
</code>
</p>

<br/>
<img src ="/images/stopping_hadoop.png" style="width:600px;height=500px">

