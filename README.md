Practical -1 
#include <GL/freeglut.h> 
#include <GL/gl.h> 
void renderFunction() 
{ 
glClearColor(0.0, 0.0, 0.0, 0.0); 
glClear(GL_COLOR_BUFFER_BIT); 
glColor3f(1.0, 1.0, 1.0); 
glOrtho(-1.0, 1.0, -1.0, 1.0, -1.0, 1.0);glBegin(GL_POLYGON); 
glVertex2f(-0.5, -0.5); 
glVertex2f(-0.5, 0.5); 
glVertex2f(0.5, 0.5); 
glVertex2f(0.5, -0.5); 
glEnd(); 
glFlush(); 
} 
int main(int argc, char** argv) 
{ 
glutInit(&argc, argv); 
glutInitDisplayMode(GLUT_SINGLE); 
glutInitWindowSize(500,500); 
glutInitWindowPosition(100,100); 
glutCreateWindow("Rameshwari Shirsath Roll No:70"); 
glutDisplayFunc(renderFunction); 
glutMainLoop(); 
return 0; 
} 
Output:
Practical -1 DDA 
 
#include <stdio.h> 
#include <stdlib.h> 
#include <GL/glut.h> 
 
float X1,Y1,X2,Y2; 
 
void init(void) 
{ 
    glClearColor(0.0,0.0,0.0,0.0); 
    glMatrixMode(GL_PROJECTION); 
    gluOrtho2D(-100.0,100.0,-100.0,100.0); 
} 
 
void setPixel(GLint x, GLint y) 
{ 
    glBegin(GL_POINTS); 
    glVertex2i(x,y); 
    glEnd(); 
} 
 
void DDA(void) 
{ 
    float dx=(X2-X1); 
    float dy=(Y2-Y1); 
    float steps; 
    float xInc,yInc,x=X1,y=Y1; 
 
    /* Find out whether to increment x or y */ 
    steps=(abs(dx)>abs(dy))?(abs(dx)):(abs(dy)); 
    xInc=dx/(float)steps; 
    yInc=dy/(float)steps; 
 
    /* Clears buffers to preset values */ 
    glClear(GL_COLOR_BUFFER_BIT); 
 
    /* Plot the points */ 
    setPixel(x,y); 
    int k;for(k=0;k<steps;k++) 
    { 
        x+=xInc; 
        y+=yInc; 
        setPixel(x,y); 
    } 
 
    glFlush(); 
} 
 
int main(int argc, char **argv) 
{ 
    printf("Enter two end points of the line to be drawn:\n"); 
    printf("\nEnter Point1(X1,Y1):\n"); 
    scanf("%f%f",&X1,&Y1); 
    printf("\nEnter Point2(X2,Y2):\n"); 
    scanf("%f%f",&X2,&Y2); 
 
    glutInit(&argc, argv); 
glutInitDisplayMode(GLUT_SINGLE|GLUT_RGB); 
glutInitWindowSize(500, 500); 
glutInitWindowPosition(0, 0); 
glutCreateWindow("Rameshwari Shirsath Roll No:70"); 
init(); 
glutDisplayFunc(DDA);   
 glutMainLoop(); 
return 0; 
} 
Output:
