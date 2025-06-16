import cv2
import numpy as np

def bilinear_interpolation(img, scale_factor):
    height, width = img.shape[:2]
    new_height = int(height * scale_factor)
    new_width = int(width * scale_factor)

    # Crear una nueva imagen vacía con las dimensiones escaladas
    result_img = np.zeros((new_height, new_width, img.shape[2]), dtype=np.uint8)

    # Coordenadas de píxeles en la imagen original y la imagen escalada
    x_ratio = float(width - 1) / (new_width - 1) if new_width > 1 else 0
    y_ratio = float(height - 1) / (new_height - 1) if new_height > 1 else 0

    for i in range(new_height):
        for j in range(new_width):
            x = int(x_ratio * j)
            y = int(y_ratio * i)
            x_diff = (x_ratio * j) - x
            y_diff = (y_ratio * i) - y

            # Fórmula de interpolación bilineal
            top_left = img[y, x] * (1 - x_diff) * (1 - y_diff)
            top_right = img[y, x + 1] * x_diff * (1 - y_diff)
            bottom_left = img[y + 1, x] * (1 - x_diff) * y_diff
            bottom_right = img[y + 1, x + 1] * x_diff * y_diff

            result_img[i, j] = top_left + top_right + bottom_left + bottom_right

    return result_img

# Cargar la imagen
input_image_path = 'ruta_de_tu_imagen.jpg'
original_image = cv2.imread(input_image_path)

# Factor de escala (cambiar según sea necesario)
scale_factor = 2.0

# Aplicar interpolación bilineal
rescaled_image = bilinear_interpolation(original_image, scale_factor)

# Mostrar la imagen original y la imagen escalada
cv2.imshow('Original', original_image)
cv2.imshow('Bilinear Interpolation', rescaled_image)
cv2.waitKey(0)
cv2.destroyAllWindows()
