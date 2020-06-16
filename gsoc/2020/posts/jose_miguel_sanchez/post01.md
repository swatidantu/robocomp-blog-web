# GSoC'20 RoboComp project: Syntax-error highlighter for LearnBlock
 
DATE
 
## About me
 
Hello! I'm José Miguel, a Computer Engineering student in Cáceres, Spain.
I've grown up with a passion for technology, and over time I've played around
with computer graphics, programming language and operating system design,
game modding, web design and programming, a bit of computer security...
I love learning something from every field I discover!

## About the Project

LearnBlock is a visual robot programming tool which eases the path towards
learning full-fledged robot programming (in Python) by putting some simpler
layers in between to make it easier for newcomers to implement their ideas and
get results quickly. I was amazed when I discovered it, not only you have a
rich visual block environment to code (and a simplified text language in the
middle), but the resulting code is portable among a variety of robots!

My goal with this project is to fix one critical flaw it has right now: lack of
proper error reporting. One of the places where helpful guiding through error
solving is most needed are learning tools, as the user may lack the intuition
or the experience a seasoned developer can apply to locate an error quickly.
The environment should not only point to the place it found a problem, but
provide some tips which make the solution clear and explain why it is required.
Then, the user not only has solved their problem, but has earned knowledge
about why the previous solution was incorrect and how to fix it in the future.

My plan is to implement a core error handling mechanism, not tied to any
representation but to an internal tree-like mirror of the code, which allows
for centralized error checking, handling and reporting; a typechecker which
annotates its nodes and finds type mismatches to further help the user locate
errors, and appropiate frontend signaling of these errors for each of the
available representations (currently, the visual block-based one and the
simplified text one)

José Miguel Sánchez García
