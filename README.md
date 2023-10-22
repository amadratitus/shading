# shading
How to implement shading in OpenGL
/*@author: Christopher Amadra Titus*/
```
#include <GL/glut.h>
#include <GL/gl.h>
#include <iostream>
#include <stdio.h>
```
```
void test(void) {
    glClearColor(1.0, 1.0, 1.0, 1.0);
    glEnable(GL_DEPTH_TEST);
}
```
```
void drawTeaPot(void) {
    glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
    glColor3f(1.0, 1.0, 1.0);
    GLfloat light_position[] = {1.0, 1.0, 1.0, 0.0};
    GLfloat mat_diffuse[] = {0.7, 0.4, 0.1, 1.0};
    glMaterialfv(GL_FRONT, GL_DIFFUSE, mat_diffuse);
    glLightfv(GL_LIGHT0, GL_POSITION, light_position);
    glEnable(GL_LIGHTING);
    glEnable(GL_LIGHT0);
    glutSolidTeapot(1.0);
    glFlush();
}
```
```
void reshape(int x, int y) {
    glViewport(0, 0, (GLsizei)x, (GLsizei)y);
    glMatrixMode(GL_PROJECTION);
    glLoadIdentity();
    gluPerspective(55.0, (GLfloat)x / (GLfloat)y, 1.0, 20.0);
    glMatrixMode(GL_MODELVIEW);
    glLoadIdentity();
    glTranslatef(0.0, 0.0, -3.0);
}
```
```
int main(int argc, char** argv) {
    glutInit(&argc, argv);
    glutInitDisplayMode(GLUT_SINGLE | GLUT_RGB | GLUT_DEPTH);
    glutInitWindowSize(800,600);
    glutInitWindowPosition(0,0);
    glutCreateWindow("Drawing a Teapot and applying color to it.");
    test();
    glutDisplayFunc(drawTeaPot);
    glutReshapeFunc(reshape);
    glutMainLoop();
    return 0;
}
```
**Final Output**
![Screenshot (173)](https://github.com/amadratitus/shading/assets/117981104/12322b81-9d4c-4de6-a2e3-aff87010d0f9)


