elixir-proc
===========

Create graphics from Elixir by calling Processing's `core.jar`
([Processing](http://processing.org/) "is an open source programming language and environment...to create images...and to teach fundamentals of computer programming within a visual context.")

To use the `Elproc` module, you have to be running `iex` with a node name:

    iex -sname some_node_name

You write your graphics code in a module that contains `setup/0` and
`draw/0` functions. Here is a short example:

    defmodule Example do
    
      def setup() do
        Elproc.background([255])
      end
    
      def draw() do
        Elproc.rect([100, 100, 50, 50])
        Elproc.fill([255, 0, 0])
        Elproc.ellipse([125, 125, 30, 40])
        Elproc.no_loop()  # this prevents redrawing 60 times per second
      end
    end

To start the sketch, call `Elproc.sketch/2` with the module name
and the sketch size:

    Elproc.sketch(example, [300, 300])

There are two sample modules with this code. The first one draws a
simple house and sun; the second draws a circle that follows the mouse.

    Elproc.sketch(house, [300, 300])
    Elproc.sketch(mouse_movement, [200, 200])
