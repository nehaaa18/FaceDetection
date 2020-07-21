# FaceDetection

package com.JFaceDetection;
import org.opencv.core.Mat;
import org.opencv.core.MatOfRect;
import org.opencv.core.Rect;
import org.opencv.core.Scalar;
import org.opencv.core.Point;
import org.opencv.core.Core;
import org.opencv.imgcodecs.Imgcodecs;
import org.opencv.imgproc.Imgproc;
import org.opencv.objdetect.CascadeClassifier;

public class JFaceDetection {
	
	public static void main(String[] args)
	{
		System.loadLibrary(Core.NATIVE_LIBRARY_NAME);
		
		String imgFile="img/2.jpg";
	    Mat src	=Imgcodecs.imread(imgFile);
	    
	    
	    
	    String xmlFile="xml/lbpcascade_frontalface_improved.xml";
	    CascadeClassifier cc=new CascadeClassifier(xmlFile);
	    
	    MatOfRect faceDetection=new MatOfRect();
	    cc.detectMultiScale(src, faceDetection);
	    
	    System.out.println(String.format("Detected faces: %d", faceDetection.toArray().length));
	    
	    for (Rect rect :faceDetection.toArray())
	    {
	    	Imgproc.rectangle(src,new Point(rect.x,rect.y),new Point(rect.x+rect.width,rect.y+rect.height), new Scalar(0,0,255),3);
	    }
	   Imgcodecs.imwrite("img/2 out.jpg", src);
	   System.out.println("Image Detection Finished");
	   
	}
	

}
