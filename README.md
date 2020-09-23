<div align="center">

## Flicker Free Applet


</div>

### Description

This Applet displays Flicker free drawing thru Double Buffering technique. This article is an excerpt from the Complete Reference of JAVA. Have Fun. If you vote for me that would be great for me but it not at all necessary.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Jayant Mukherjee](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/jayant-mukherjee.md)
**Level**          |Intermediate
**User Rating**    |3.8 (15 globes from 4 users)
**Compatibility**  |Java \(JDK 1\.1\), Java \(JDK 1\.2\)
**Category**       |[Applet](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/applet__2-81.md)
**World**          |[Java](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/java.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/jayant-mukherjee-flicker-free-applet__2-3875/archive/master.zip)





### Source Code

```
<pre style="font-size:9pt; background-color:#F3F3F3;">
/* A simple Double Buffering example by Jayant Mukherjee (courtesy: Complete Reference) */
/* Another way of doing the same is described by Wayne McKenzie on PSC */
import java.awt.*;
import java.applet.*;
import java.awt.image.*;
import java.awt.event.*;
public class DblBuffr extends Applet implements MouseMotionListener{
  int ax,ay;
  Dimension dSize;
  Image dblBuffImg; //Off Screen
  Graphics dblBuffer; //Off Screen Graphics
  public void init(){
    dSize = this.getSize();
    dblBuffImg = this.createImage(dSize.width, dSize.height);
    dblBuffer = dblBuffImg.getGraphics();
    addMouseMotionListener(this);
    this.setBackground(Color.yellow);
  }
  public void mouseDragged(MouseEvent em){} //Not used, but required
  public void mouseMoved(MouseEvent em)
  {
    ax = em.getX();
    ay = em.getY();
    this.paint(this.getGraphics()); //Fast repainting
  }
  public void update(){} //Overriding, for Flicker Free Drawing
  public void paint(Graphics g)
  {
    dblBuffer.clearRect(0, 0, dSize.width, dSize.height);
    for(int i=0; i&lt;=dSize.width; i=i+10)
    {
      dblBuffer.drawLine(ax,ay,i,0); //Top edge
      dblBuffer.drawLine(ax,ay,i,dSize.height); //Bottom edge
    }
    for(int i=0; i&lt;=dSize.height; i=i+10)
    {
      dblBuffer.drawLine(ax,ay,0,i); //Left edge
      dblBuffer.drawLine(ax,ay,dSize.width,i); //Right edge
    }
    g.drawImage(dblBuffImg, 0, 0, null);
  }
}
</pre>
```

