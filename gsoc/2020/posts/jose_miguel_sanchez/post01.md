# GSoC'20 RoboComp project: Syntax-error highlighter for LearnBlock
 
DATE
 
## About me
 
Hello! I'm José Miguel, a Computer Engineering student at the University of
Extremadura in Cáceres, Spain. I've grown up with a passion for technology.
Over time I've played around with computer graphics, programming language
theory, operating system design, game modding, web design and programming and a
bit of computer security... I love learning something from every field I
discover!

## About the Project

LearnBlock is a visual robot programming tool that eases the path towards
learning full-fledged robot programming (in Python). Putting some more
straightforward layers in between makes it easier for newcomers to implement
their ideas and get results quickly.

I was amazed when I discovered LearnBlock. not only you have a productive
visual block environment to code (and a simplified text language in the
middle), but the resulting code is portable among a variety of robots!

My goal with this project is to fix one critical flaw it has right now: lack
of proper error reporting. In learning tools, it is crucial to have useful
guidance through error resolution, since the target user usually lacks the
intuition or expert that an experience developer has. The environment should
not only point to the place where it found a problem, but also provide some
tips which make the solution clear and explain why it is required. Then, the
user has not only solved their problem but has also learned why the
previous solution was incorrect and how to fix it in the future.

I plan to implement a core error handling mechanism, not tied to any
representation but to an internal tree-like mirror of the code, which allows
for centralized error checking, handling and reporting. A typechecker which
annotates its nodes and finds type mismatches to help further the user locate
errors, as well as, an appropiate frontend signaling of these errors for each
of the available representations (currently, the visual block-based one and
the simplified text one).

José Miguel Sánchez García
