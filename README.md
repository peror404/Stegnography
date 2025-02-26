
# Steganography in Images (Message Encryption & Decryption)

This project demonstrates a basic implementation of **steganography**, the art of hiding secret messages within an image. Using this technique, you can encrypt a secret message and hide it inside the pixel data of an image. The message can later be extracted using a passcode to ensure security.

## Features

- **Hide Secret Message**: You can input a secret message and a passcode, and the message will be hidden in the image file.
- **Extract Hidden Message**: A passcode is required to decrypt and reveal the hidden message.
- **Simple Image-based Steganography**: The message is encoded in the image pixels' blue channel, and the first pixel stores the message length.
- **Password Protection**: Decryption of the message requires the correct passcode, ensuring that only authorized users can access the hidden message.

## Prerequisites

To run this code, you will need:
- Python 3.x
- OpenCV library (`cv2`)
- NumPy library (`numpy`)

You can install the necessary dependencies using the following command:

```bash
pip install opencv-python numpy
```

## How it Works

### Step 1: Encrypt the Message

1. You will be prompted to input:
   - **The secret message** you want to hide.
   - **A passcode** to protect the message.
   
2. The program reads the provided image and stores the length of the message in the first pixel's red channel.
3. The secret message is encoded into the image by modifying the pixel values in the blue channel, starting from the second pixel onward.
4. The modified image is saved as `encryptedImage.jpg`, and the user can open it to see the image with the hidden message.

### Step 2: Decrypt the Message

1. To decrypt the message, the user will be prompted to input the **decryption passcode**.
2. The program verifies the passcode. If it's correct, the hidden message is extracted from the image and displayed.
3. If the passcode is incorrect, the program will display an error and deny access to the hidden message.

### Limitations
- The size of the secret message must be smaller than the available space in the image (height * width).
- The message is hidden in the blue channel of the image, and the first pixel stores metadata (message length).

## Code Structure

- **Image Reading**: The image is read using OpenCV's `cv2.imread()` method.
- **Message Encoding**: The secret message is converted into a list of ASCII values using Python's `ord()` function. These values are encoded into the image's pixel values.
- **Message Decoding**: The program extracts the message by reversing the encoding process, starting from the first pixel (excluding the first channel).
- **Encryption and Decryption Logic**: The encryption and decryption processes involve modifying the pixel data and using a passcode to ensure only authorized decryption.

## How to Run

1. **Prepare an Image**: Choose an image you want to use for hiding the message.
2. **Encrypt the Message**: Run the script to input the secret message and passcode. The encrypted image will be saved as `encryptedImage.jpg`.
3. **Decrypt the Message**: Run the script again, input the decryption passcode, and the hidden message will be revealed.

### Sample Workflow

#### Encrypting a Message

```bash
Enter secret message: This is a secret!
Enter a passcode: mypassword
```

After encryption, the image `encryptedImage.jpg` will be created.

#### Decrypting a Message

```bash
Enter passcode for decryption: mypassword
```

If the passcode is correct, the message will be displayed:

```bash
Decryption successful! Message: This is a secret!
```

## Security

The system uses a passcode for encryption and decryption to ensure that only authorized users can access the hidden message. However, this is a basic implementation and should not be considered highly secure for critical use cases. It's recommended to use advanced encryption techniques for real-world applications.

## Notes

- This code is intended as an educational demonstration of basic steganography.
- The size of the message is limited by the image's resolution. If the message is too large, it will not fit within the image.
