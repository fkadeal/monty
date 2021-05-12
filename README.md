# 0x19. C - Stacks, Queues - LIFO, FIFO
<h3>The Monty language</h3>

<p>Monty 0.98 is a scripting language that is first compiled into Monty byte codes (Just like Python). It relies on a unique stack, with specific instructions to manipulate it. The goal of this project is to create an interpreter for Monty ByteCodes files.</p>

<p><strong>Monty byte code files</strong></p>

<p>Files containing Monty byte codes usually have the <code>.m</code> extension. Most of the industry uses this standard but it is not required by the specification of the language.
There is not more than one instruction per line. There can be any number of spaces before or after the opcode and its argument:</p>

<pre><code>julien@ubuntu:~/monty$ cat -e bytecodes/000.m
push 0$
push 1$
push 2$
  push 3$
                   pall    $
push 4$
    push 5    $
      push    6        $
pall$
julien@ubuntu:~/monty$
</code></pre>

<p>Monty byte code files can contain blank lines (empty or made of spaces only, and any additional text after the opcode or its required argument is not taken into account:</p>

<pre><code>julien@ubuntu:~/monty$ cat -e bytecodes/001.m
push 0 Push 0 onto the stack$
push 1 Push 1 onto the stack$
$
push 2$
  push 3$
                   pall    $
$
$
                           $
push 4$
$
    push 5    $
      push    6        $
$
pall This is the end of our program. Monty is awesome!$
julien@ubuntu:~/monty$
</code></pre>

<p><strong>The monty program</strong></p>

<ul>
<li>Usage: <code>monty file</code>

<ul>
<li>where <code>file</code> is the path to the file containing Monty byte code</li>
</ul></li>
<li>If the user does not give any file or more than one argument to your program, print the error message <code>USAGE: monty file</code>, followed by a new line, and exit with the status <code>EXIT_FAILURE</code></li>
<li>If, for any reason, it&rsquo;s not possible to open the file, print the error message <code>Error: Can&#39;t open file &lt;file&gt;</code>, followed by a new line, and exit with the status <code>EXIT_FAILURE</code>

<ul>
<li>where <code>&lt;file&gt;</code> is the name of the file</li>
</ul></li>
<li>If the file contains an invalid instruction, print the error message <code>L&lt;line_number&gt;: unknown instruction &lt;opcode&gt;</code>, followed by a new line, and exit with the status <code>EXIT_FAILURE</code>

<ul>
<li>where <line_number> is the line number where the instruction appears.</li>
<li>Line numbers always start at 1</li>
</ul></li>
<li>The monty program runs the bytecodes line by line and stop if either:

<ul>
<li>it executed properly every line of the file</li>
<li>it finds an error in the file</li>
<li>an error occured</li>
</ul></li>
<li>If you can&rsquo;t malloc anymore, print the error message <code>Error: malloc failed</code>, followed by a new line, and exit with status <code>EXIT_FAILURE</code>.</li>
<li>You have to use <code>malloc</code> and <code>free</code> and are not allowed to use any other function from <code>man malloc</code> (realloc, calloc, &hellip;)</li>
</ul>

</div>
