---
layout: post
title: Vertex and Index Buffers Introduction
tags: [vertex, index, buffer]
image: /assets/img/pexels/triangles.jpg
excerpt_separator: <!--more-->
---

A rendering engine draws images of the application to the screen by using vertex and index buffers. The models used in games are created out of triangles, which the rendering engine uses to draw. A vertex buffer is a list of coordinates used for drawing triangles. The index buffer helps save memory by reducing the need to store shared vertices in the vertex buffer. 

<!--more-->

![Runner]({{ site.baseurl }}/assets/img/pexels/triangles.jpg)
<p align="center"><i>Triangles in a 3D model</i></p>

## Vertex and Index Buffer Square

![Runner]({{ site.baseurl }}/assets/img/pexels/square.jpg)
<p align="center"><i>Vertices of two triangles</i></p>

To understand how 3D models are drawn, it helps to start with something easier than a 3D model: a square. The vertex buffer contains a list of vertices used to draw triangles to the screen. For example, for drawing a square in 2D it could list every vertex of the two triangles:

	float vertexBuffer[] = {
		-1,  1 // Bottom left triangle
		-1, -1,
		 1, -1, 
		-1,  1, // Top right triangle
		 1, -1,
		 1,  1
	}

The coordinates (-1, 1), (-1, -1), and (1, -1) form the bottom left corner of the square. The coordinates (-1, 1), (1, -1), and (1, 1) form the top right corner of the square. Together this could be used to tell the graphics card to render two triangles to the screen. Can you think of a more efficient way to tell the graphics card what triangles to render?

Notice how there are duplicate vertices. Both (-1, 1) and (1, -1) are used twice. That is wasted memory. In big detailed 3D models that can add up to a lot of waste. Index buffers are used to save memory by listing indices into the vertex buffer, rather than giving an explicit vertex buffer to the renderer. If we were to use a vertex buffer and index buffer, it would look like so:

	float vertexBuffer[] = {
		-1,  1, // Top left corner
		-1, -1, // Bottom left corner
		 1, -1, // Bottom right corner
		 1,  1  // Top right corner
	}

	unsigned short indexBuffer[] = {
		0, 1, 2 // Bottom left triangle
		0, 2, 3 // Top right triangle
	}

Instead of 12 floats (48 bytes) to draw two triangles, we used 8 floats and 6 unsigned shorts (44 bytes) for a total of 4 bytes saved to draw the same thing. Although this simple example is only 4 bytes of savings, real 3D models contain much more information and the memory savings can be a lot better. With large complicated models that adds up to a lot of saved memory.

## Conclusion

There is a lot more to rendering than index and vertex buffers, but hopefully this can be your introduction and catalyst to learning more about graphics programming. There are a lot of fancy sounding words in graphics programming but you can do it. Learn it one concept at a time. You can do it.