# teapot
teapot program
// ChaiCup.cpp : Defines the entry point for the console application.
//

#include "stdafx.h"
#include<GL/glut.h>
void init()
{
glMatrixMode(GL_PROJECTION);
glLoadIdentity();
glOrtho(-4, 4, -4, 4, -10, 10);
glMatrixMode(GL_MODELVIEW);
glEnable(GL_DEPTH_TEST);
glShadeModel(GL_SMOOTH);
glEnable(GL_LIGHTING);
glEnable(GL_LIGHT0);
glEnable(GL_NORMALIZE);
}
void wall()
{
 // The below code is used to create the
 glPushMatrix();
 glTranslatef(1, -1, 1);
 glScalef(2, 0.05, 2);
 glutSolidCube(2);
 glPopMatrix();
 // The below code is used to create the
 glPushMatrix();
 glTranslatef(-1, 1, 1);
 glScalef(0.05, 2, 2);
 glutSolidCube(2);
 glPopMatrix();
 // The below code is used to create the
 glPushMatrix();
 glTranslatef(1, 1, -1);
 glScalef(2, 2, 0.05);
 glutSolidCube(2);
 glPopMatrix();
}
void table()
{
 // The below code is used create the top
 //face of the table
 glPushMatrix();
 glTranslatef(1, -0.4, 1);
 glScalef(1, 0.05, 1);
 glutSolidCube(2);
 glPopMatrix();
 // The Front-Left leg
 glPushMatrix();
 glTranslatef(0.15, -0.7, 1.85);
 glScalef(0.1, 0.5 / 2, 0.1);
 glutSolidCube(2);
 glPopMatrix();
 // The Front-Right leg 
 glPushMatrix();
 glTranslatef(1.85, -0.7, 1.85);
 glScalef(0.1, 0.5 / 2, 0.1);
 glutSolidCube(2);
 glPopMatrix();
 // The Back-Right leg
 glPushMatrix();
 glTranslatef(1.85, -0.7, 0.15);
 glScalef(0.1, 0.5 / 2, 0.1);
 glutSolidCube(2);
 glPopMatrix();
 // The back-Left leg
 glPushMatrix();
 glTranslatef(0.15, -0.7, 0.15);
 glScalef(0.1, 0.5 / 2, 0.1);
 glutSolidCube(2);
 glPopMatrix();
}
void tea()
{
  glPushMatrix();
  glTranslatef(1, 0, 1);
  glRotatef(45, 0, 1, 0);
  glutSolidTeapot(0.5);
  glPopMatrix();
}
void display(void)
{
  float amb[] = { 0.7, 0.8, 0.2 };
  float spec[] = { 0.2, 0.7, 0.6 };
  float pos[] = { 3, 2, 1 };
  glClear(GL_COLOR_BUFFER_BIT |
  GL_DEPTH_BUFFER_BIT);
  glLoadIdentity();
  glMaterialfv(GL_FRONT,
  GL_AMBIENT_AND_DIFFUSE, amb);
  glMaterialfv(GL_FRONT, GL_SPECULAR,spec);
  glMaterialf(GL_FRONT, GL_SHININESS,50.0);
  glLightfv(GL_LIGHT0, GL_POSITION, pos);
  gluLookAt(2.5, 0.5, 2, 0, 0, 0, 0, 1,0);
  wall();
  table();
  tea();
  glFlush();
}
int main()
{
  glutInitDisplayMode(GLUT_SINGLE |
  GLUT_DEPTH);
  glutInitWindowSize(600, 600);
  glutCreateWindow("teapot");
  init();
  glutDisplayFunc(display);
  glutMainLoop();
  return 0;
}

