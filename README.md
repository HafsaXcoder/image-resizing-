import cv2

def resize_image(input_image, output_image, width=1000, height=700):
    # Read input image
    image = cv2.imread(input_image)

    if image is None:
        print(f"Error: Unable to read image '{input_image}'. Please check the file path/integrity.")
        return

    # Resize image
    if width and height:
        resized_image = cv2.resize(image, (width, height))
    elif width:
        aspect_ratio = width / float(image.shape[1])
        height = int(image.shape[0] * aspect_ratio)
        resized_image = cv2.resize(image, (width, height))
    elif height:
        aspect_ratio = height / float(image.shape[0])
        width = int(image.shape[1] * aspect_ratio)
        resized_image = cv2.resize(image, (width, height))
    else:
        resized_image = image

    # Save resized image
    cv2.imwrite(output_image, resized_image)
    print(f"Resized image saved as '{output_image}'.")

# Example usage:
if __name__ == "__main__":
    input_image_path = 'cyber-cat.jpg'    # Replace with your input image file path
    output_image_path = 'cyber-cat.jpg' # Replace with desired output image file path
    resize_image(input_image_path, output_image_path, width=1000)
