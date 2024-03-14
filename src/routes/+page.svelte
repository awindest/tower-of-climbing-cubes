<!--
                       
╭━━╮╱╱╱╱╭╮╱╱╱╱╱╭╮╱╭╮╱╱╱╱╱╭╮            ━╮ ╭━
╰┫┣╯╱╱╱╱┃┃╱╱╱╱╭╯╰╮┃┃╱╱╱╱╱┃┃             | |
╱┃┃╭━╮╭━╯┣━━┳━┻╮╭╯┃┃╱╱╭━━┫╰━┳━━╮       ╱ o \
╱┃┃┃╭╮┫╭╮┃┃━┫━━┫┃╱┃┃╱╭┫╭╮┃╭╮┃━━┫      ╱_____\
╭┫┣┫┃┃┃╰╯┃┃━╋━━┃╰╮┃╰━╯┃╭╮┃╰╯┣━━┃     ╱    o  \  
╰━━┻╯╰┻━━┻━━┻━━┻━╯╰━━━┻╯╰┻━━┻━━╯    (__o______)  

Yet another science experiment from Indest Labs.

Recommend viewing in Visual Source Code.
Attribution: 
Amit did a great job on this and it helped me learn scss to boot!

  The CodePen:
  https://codepen.io/amit_sheen/pen/JjzGGQR
  and youtube links for a follow-along:
  https://youtube.com/live/2gEZlTpVCBY
  https://www.youtube.com/watch?v=2gEZlTpVCBY
  
  which is based on a threejs cube:
  https://twitter.com/akella/status/1739936674228891989

  What did I do? I just replaced a lot of html with some loops.
-->
<div class="scene">
    {#each Array(12) as _, index (index)}
        <div class="column">
            {#each Array(6) as _, index (index)}
                <div class="box"><i></i><i></i><i></i><i></i><i></i><i></i></div>
            {/each}
        </div>
    {/each}
</div>

