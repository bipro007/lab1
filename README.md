1.At first we need to creat a windows,the deal with the dependencies (libraries) : after that we neeed basics to display messages in the console:

    #include <GL\freeglut.h>
    #include <GL\glew.h> 
    #include <iostream>
    #include <glm/vec3.hpp>
  
Second we initialize GLUT, first one is a pointer to the argument line and the second one is to the argument array.
  
    int main(int argc, char** argv)
  
Third LUT. GLUT_DOUBLE Enables double buffering of the color buffer used for the final render target (such as the screen) and the following functions that set the window options and give the window its title.
   
     glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGBA);
  
Fourth for interacting with the window system GLUT is responsible and provides us with various callback options. as far, we're only using one, most importantly, one that makes 1 frame. GLUT regularly calls this function.
  
    glutDisplayFunc(RenderSceneCB);

 Fifth glClearColor function specifies clear values for the color buffers 
  
    glClearColor(0.0f, 0.0f, 0.8f, 0.0f);
  
 Sixth this function will cause all the GLUT functions which control functions to be repeated when necessary, and its a smart loop, in other words, which giving GLUT control over the program,
    
    glutMainLoop();
   
Seventh What we do in our render function is to clear the frame buffer (using the old color set, try changing it). The second function tells GLUT to switch between the background buffer and the frame buffer. The next call will be rendered in the current frame buffer and the background buffer will be rendered.  
  
    glClear(GL_COLOR_BUFFER_BIT);
    glutSwapBuffers();
  
  Creating a triangle
  At firt we start by drawing the triangle point and then the vertex points
  
      Vertices[0] = glm::vec3(0.0f, 0.0f, 0.0f)
  
      glm::vec3 Vertices[3]{
	   glm::vec3(-1.0f, -1.0f, 0.0f),
	   glm::vec3(1.0f, -1.0f, 0.0f),
	   glm::vec3(0.0f, 1.0f, 0.0f)
	};
  
 Second here we take the size of the data in bytes and the pattern that indicates the vertex array address and data usage.
  
      glEnableVertexAttribArray(0);
  
Third we specifies the index of the vertex to be activated,or we can also specify which ones are deactivated  
     
       glEnableVertexAttribArray(0);
      glDisableVertexAttribArray(0);
  
Forth instead of calling each individual vertices, normal, texture coordinates, edge flags, or a GL method for passing colors, we can specify individual arrays of vertices, normals, and colors, and use them to create a sequence of primitives. When glDrawArrays is called, it first counts the sequential elements from each active array to create a sequence of geometric primitives, starting with the element. Mode specifies what kind of primitives are created and how the elements of the array create those primitives. Vertex features modified by glDrawArrays have an indefinite value after the return of glDrawArrays. Features that are not modified are well defined  
  
      glDrawArrays(GL_POINTS, 0, 1);
      glDrawArrays(GL_TRIANGLES, 0, 3);
