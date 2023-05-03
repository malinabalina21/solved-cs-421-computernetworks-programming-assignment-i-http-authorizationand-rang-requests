Download Link: https://assignmentchef.com/product/solved-cs-421-computernetworks-programming-assignment-i-http-authorizationand-rang-requests
<br>
1) Introduction

In   this      programming assignment,    you      are      asked  to         implement     a          program         in         either  <strong>Java    or Python           3</strong>.         You     should code    a          program         that     downloads     and      processes       data     that     is         obtained from    an        HTTP  Server.

The            goal     of         the      assignment    is         to         make   you      familiar           with    the      HTTP  Protocol          and      TCP socket programming.            You     must   implement     your    program         using   either  the      <strong>Java    Socket            API      of        the JDK     </strong>or        the<strong>      Socket            </strong>package          in         your    default Python            distribution.   If         you      have    any      doubt about  what   to         use      or        not      to         use,     please contact           your    teaching         assistant         Ayhan Okuyan           at<strong> ayhan.okuyan[at]bilkent.edu.tr.</strong> For      Python,           the      use      of         any      class/function            from    <strong>http    or        the requests        package         is         prohibited.   </strong>

When        preparing       your    project            please keep    in         mind   that     your    projects          will      be        Girst    evaluated by        a          computer       program.        Any     problems        in         the      formatting      can      create problems        in         the grading.          Errors caused by        incorrectly     naming           the      project            Giles    and      folder  structure        will      cause  you to         lose     points.

<h1>2) SpeciUications</h1>

The      server program         that     is         provided        to         you      (in       Python            3)        uses    a          HTTP/1.1 similar application     layer   protocol          that     uses    TCP     underneath    to         communicate with    the      client.  In        server side, there   are      three   entities           that     you      will      separately      download       and      process.          For      easy    understanding, this      project            is         divided           into     three   parts,  all        contributing   to         each    other.  It         is         suggested       that you      start    from    the      Girst    part     and      continue         sequentially.  In        order  to         work   with    these   problems, Girst    you      will      be        running          the      server program.        In        order  to         run      the      program         use      the following        command       in         the      homework     folder  via       terminal.         Note    that     one      should download       the appropriate    Python            3          software.        This     server code    is         written           in<strong>         Python           3.7.7.              </strong>

python3 serv.py

This     program         is         written           such    that     it          opens  a          socket and      creates            a          listening         port on        your    local    machine         on        port     8000   (http://localhost:8000/).                 If         you      receive            a          binding error   while   running          this      program,        port     8000   may     be        used    by        another           process,          so        consider changing         it.

<h1>A.First          HTTP            Connection            and    TCP   Socket          Programming</h1>

This     Girst    part     of         the      project            asks     you      to         create a          TCP     Socket as        an        HTTP  client  and connect           it          to         the      socket that     the      server program         is         listening.                    Then   retrieve          the webpage         data     by        sending           a          simple HTTP  GET     request,          issued as        follows:

<table width="269">

 <tbody>

  <tr>

   <td width="240">GET &lt;ENTITY&gt; HTTP/1.1r
</td>

   <td width="29"></td>

  </tr>

  <tr>

   <td colspan="2" width="269">Host: &lt;SERVER HOST&gt; r
r
</td>

  </tr>

 </tbody>

</table>

Where &lt;ENTITY&gt;      is         the      Gilename        that     you      are      required         to         enter   with    a          “/“       in         the beginning       to         indicate          that     and      &lt;SERVER        HOST&gt; is         the      domain           URL     that     you      are      trying  to reach  e.g.      localhost:8000/.<strong>                    </strong>When  a          webpage         entity  is         requested       for       the      Girst    time,   its ‘index.html’    page    is                     requested,      or        you      can      simply leave   the      &lt;ENTITY&gt;      as        ‘/‘        to         request this      page.<strong>   Once   the      content          is         retrieved,      store  it         as        an       HTML Uile     with    the      name ‘index2.html’.           </strong>Then   you      need    to         extract the      information    of         the      entity  that     you      will      try       to obtain next,    hidden in         the      HTML code.   Parsing           and      obtaining        the      entity  name   is         part     of         the assignment    and      your    grade  will      be        deducted        in         the      absence          of         it.<strong>         In        the      report, provide          a          brief   explanation  as        to        how    the      GET     requests        and     corresponding         responses operate.         </strong>

<h1>B. HTTP Authentication</h1>

In         the      second            part,    you      are      asked  to         reach  and      download       the      content           whose name   you have    covered          in         the      previous         part.    However,        this      part     of         the      site      is         protected       with    a Basic   Authorization scheme.          For      further            information,   examine          the      <a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication">HTTP</a><a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication">  </a><a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication">Authentication           page</a>.

First,   try       to         access the      page    using   the      method           you      have    followed         in         the      previous         part. Then   use      a          GET     request           with    a          <a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Authorization">Basic   Authorization</a>             header.           You     are      provided        the username       and      password,      <strong>‘bilkentstu’</strong>   and      <strong>‘cs421s2021</strong>‘            respectively.  Use      these   credentials     in         the form    <strong>&lt;USERNAME&gt;:&lt;PASSWORD&gt;</strong>       and      obtain a          base64            encoding        as        the      authentication           key.     You may     face     the      following        response        codes  from    the      server program.




<table width="600">

 <tbody>

  <tr>

   <td width="200"><strong>STATUS CODE</strong></td>

   <td width="200"><strong>NAME </strong></td>

   <td width="200"><strong>FUNCTION</strong></td>

  </tr>

  <tr>

   <td width="200"><strong>200</strong></td>

   <td width="200">OK</td>

   <td width="200">The request has succeeded.</td>

  </tr>

  <tr>

   <td width="200"><strong>401</strong></td>

   <td width="200">Unauthorized</td>

   <td width="200">The client must authenticate itself to get the requested response.</td>

  </tr>

  <tr>

   <td width="200"><strong>403</strong></td>

   <td width="200">Forbidden</td>

   <td width="200">The client does not have access rights to the content; that is, it isunauthorized, so theserver is refusing to give the requested resource.</td>

  </tr>

  <tr>

   <td width="200"><strong>404</strong></td>

   <td width="200">Not Found</td>

   <td width="200">The server cannot find the requested page. </td>

  </tr>

 </tbody>

</table>

<strong>In        your   report answer          these  questions.     </strong>

<ul>

 <li>Why did the      Girst    attempt          resulted          with    an        error   code?  Why    do        we       use      authorization?</li>

 <li>Why do we       use      an        encoding        when   sending           the      authorization request?</li>

</ul>

Save    the      HTML Gile     obtained         from    this      page    and      save    it          as        <strong>‘protected2.html’.   </strong>Then,  repeat the previous         part     and      extract the      name   of         the      entity  that     will      be        processed       in         the      following        part. Parsing           and      obtaining        the      entity  name   is         part     of         the      assignment    and      your    grade  will      be deducted        in         the      absence          of         it.<strong>         </strong>

<h1>C. HTTP       Range           Requests</h1>

When  downloading  or        streaming       particularly    large   entities           from    the      web     e.g       videos, It         may     not      be feasible           to         do        it          with    a          single  GET     request.          For      these   types   of         occasions,       <a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Range_requests">Range Requests</a> are      used    to         retrieve          parts   of         the      data.    In        order  to         be        able     to         do        that,    you      will send    a          <strong>HEAD request          </strong>to         retrieve          information    on        the      length of         the      data     with    the      following format.

<table width="269">

 <tbody>

  <tr>

   <td width="250">HEAD &lt;ENTITY&gt; HTTP/1.1r
</td>

   <td width="19"></td>

  </tr>

  <tr>

   <td colspan="2" width="269">Host: &lt;SERVER HOST&gt; r
r
</td>

  </tr>

 </tbody>

</table>

Use      this      request           to         get       the      information    on        the      text     entity  whose name   is         obtained         in         the previous         part     and      the      ‘index.html’    Gile.<strong>     In        your   report,           explain          what   the      received        headers do       and     compare        the      two.    </strong>After   covering         the      length, you      should write   a          code    to         download       the text     Gile     in         <strong>ranges            [10,100,1000,10000,15000]        bytes  </strong>and      save    the      total    download       time    for       each case<strong>.    In        your   report,           provide          the      execution      times  and     the      plot     of        execution      time    vs. range. Comment      on       the      reason           why    the      graph has      the      shape that     you     obtained.       Discuss          on what   would happen          if         you     try       to        download      the      text     Uile     with    a          single GET     request          (not using  range requests).     Also    give    a          brief   description   of        the      challenges     you     have   faced  during            the implementation      process.         </strong>Since   HTTP  is         a          stateless         protocol,         client  should be        aware and      track   the arrival of         the      last      part     of         the      Gile     with    the      information    derived           from    the      incoming        headers.

Note    that     the      server program         is         adopted          for       single  client  use      and      inherent         persistent       connection. This     means after    connecting     the      client,  you      won’t  be        able     to         connect           with    another           client  and      also you      can      use      the      open   connection     to         send    and      retrieve          data     more   than    once,   without           the need    of         another           client.  Also     note    that,    HTTP  is         a          synchronous  protocol          which  waits   for       the response        from    the      server before sending           another           request           (excluding      HTTP2.0).       Save    all        of         the obtained         Giles    with    the      format ‘<strong>big&lt;RANGE&gt;.txt’     </strong>where &lt;RANGE&gt;       is         the      used    range  value   for       that execution<strong>.      </strong>

<strong>                                                           </strong>The       responses       you      may     observe          in         this      part     are      as        follows.

<table width="600">

 <tbody>

  <tr>

   <td width="200"><strong>STATUS CODE</strong></td>

   <td width="200"><strong>NAME </strong></td>

   <td width="200"><strong>FUNCTION</strong></td>

  </tr>

  <tr>

   <td width="200"><strong>206</strong></td>

   <td width="200">Partial Content</td>

   <td width="200">This response code is used when the <a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Range">Range</a> header is sent from the client to request only part of a resource.</td>

  </tr>

  <tr>

   <td width="200"><strong>416</strong></td>

   <td width="200">Requested Range is not Satisfiable</td>

   <td width="200">The requested byte range is not available and is out of bounds.</td>

  </tr>

  <tr>

   <td width="200"><strong>404</strong></td>

   <td width="200">Not Found</td>

   <td width="200">The server can not find the requested page. </td>

  </tr>

 </tbody>

</table>

The      persistent       connection     is         established     with    the      use      of         ‘<a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Connection">Connection</a><a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Connection">’</a>   header in         HTTP1.1.        The connection     stays   active  when   connection     is         ‘<a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Keep-Alive">keep-alive</a><a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Keep-Alive">’</a>     until    the      status  is         changed          to         ‘close’. However, the      connection     between         the      server is         implemented as        a          persistent       one      inherently      in         this assignment    and      in         order  to         close   the      connection     with    the      server, it          is         necessary       to         send    an EXIT    request           which  is         deGined          as        follows.

<table width="269">

 <tbody>

  <tr>

   <td width="173">EXIT HTTP/1.1r
</td>

   <td width="96"></td>

  </tr>

  <tr>

   <td colspan="2" width="269">Host: &lt;SERVER HOST&gt; r
r
</td>

  </tr>

 </tbody>

</table>

<h1>3) Running your  Program</h1>

Your    program         must   be        <strong>a          console          application</strong>   (no      graphical        user    interface,        GUI,     is         allowed) and      should be        named as<strong>        httpclient.py </strong>or<strong>        httpclient.java</strong>         based  on        your    preference     of         language. Your    program         should not      take     any      argument       from    the      command       line.     You     are      free     and encouraged    to         place   print   statements     in         your    code    to         describe         the      functionality. <strong>Please note    that     you must   run     your   program        after   you     start   the      server program</strong>.

<h1>4) Final        Remarks</h1>

<ul>

 <li><strong>Please contact your   teaching        assistant        Ayhan Okuyan          </strong></li>

</ul>

<strong>(ayhan.okuyan[at]bilkent.edu.tr)           if         you     have   any     questions      about the      assignment.  </strong>

<ul>

 <li><strong>Do not      forget to        check the      response       message        after   sending         each   command      to        see      if            your   code   is         working         properly        </strong>and      debug it          if          it          is              Note    that     the            server cannot detect all        the      errors that     you      make;  therefore,       you      might  have    to         experiment    to            make   sure    that     you      correct            all        your    errors.</li>

 <li>You can      modify            the      source code    of         the      server for       experimental        However,        do        not            forget  that     your    projects          will      be        evaluated       based  on        the      version           we       provide.</li>

 <li>You might  receive            some   socket exceptions      if          your    program         fails     to         close   sockets           from    its            previous                  In        that     case,    you      can      manually        shut     down  those   ports   by        waiting            for       them   to         timeout,          restarting       the      machine,         etc.</li>

 <li>Remember that     all        the      commands     must   be        constructed    as        strings and      encoded          with    US-ASCII</li>

 <li><strong>Please put the      downloaded Uiles   the      under the      same  directory       with    the      server and     client  </strong></li>

</ul>

<ul>

 <li></li>

</ul>