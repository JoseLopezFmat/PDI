import cv2
import numpy as np

def interpolacion_bilineal(img, nuevo_altura,nuevo_anchura):
    altura, anchura = img.shape[:2]
    nueva_imagen = np.zeros((nuevo_altura,nuevo_anchura,3),
                            dtype=np.uint8)
    factor_x = float(altura)/nuevo_altura
    factor_y = float(anchura)/nuevo_anchura 
    for x in range(nuevo_altura):
        for y in range(nuevo_anchura):
            x_original = x * factor_x
            y_original = y * factor_y
            x1 =int(x_original)
            y1 =int(y_original)
            x2 = min(x1+1,altura-1)
            y2 = min(y1+1,anchura-1)
            dx = x_original-x1
            dy = y_original-y1
            nueva_imagen[x , y] = ((1-dy)*((1-dx)*img[x1,y1]+
                                           img[x1,y2]*dx)+
                                   ((1-dx)*img[x2,y1]+
                                    img[x2,y2]*dx)*dy)
    return nueva_imagen

ruta_imagen = 'lena256color.png'
ruta_resultado ='ImResul.png'
imagen = cv2.imread(ruta_imagen)


if imagen is not None:
    
   image_interve = interpolacion_bilineal(imagen,128,128)
   cv2.imshow('ImagenOriginal', imagen)
   cv2.imshow('ImagenInterpolada', image_interve)
   cv2.waitKey(0) 
   cv2.destroyAllWindows()
   cv2.imwrite(ruta_resultado, image_interve)

else:
    print('No se pudo cargar la imagen.')
