
Binary File Creation Guide
==========================

This documentation provides a detailed guide on how to create a binary file using Python. This guide demonstrates key concepts such as converting sequences to bytes and writing those bytes into a file.

Overview
--------

In this guide, we will cover:

- Setting up the necessary Python environment
- Defining sequences and padding them
- Converting sequences to byte format
- Writing data to a binary file
- Viewing and debugging the output

Step-by-Step Instructions
-------------------------

1. **Setup and Imports**

   To work with sequences and convert them to binary, we need the `numpy` library. Install numpy if you haven't already by running::

      pip install numpy

   In your Python script, import numpy with::

      import numpy as np

2. **User-Defined Variables**

   To create a binary file, you first define the sequences you want to write into that file.
   For example, we have two sequences: `pol` and `on_`. The `pol` sequence represents the polarity, and the `on_` sequence is for "active low" (off) status. Additionally, define the filename for the binary file::

      # Define the filename (adjust as needed)
      filename = "PRBS_4.usm"
      pol = [1, 1, 0, 0, 0, 1, 0, 0, 1, 1, 0, 1, 0, 1, 1]
      on_ = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]

3. **Padding Sequences**

   Since byte representation typically requires sequences of length that are multiples of 8, we need to pad these sequences with zeros until their length matches a multiple of 8::

      slen = len(pol)  # Length of original sequence
      apol = 8 - len(pol) % 8  # Calculate padding
      pol.extend([0] * apol)  # Pad pol sequence with zeros
      on_.extend([0] * apol)  # Pad on_ sequence with zeros

4. **Convert Sequences to Bytes**

   We can then convert the padded sequences into a byte array using `numpy.packbits()`. This function takes a list of bits and converts them to an equivalent byte array::

      pol_bytes = np.packbits(np.array(pol), bitorder='big')
      on_bytes = np.packbits(np.array(on_), bitorder='big')

   Here, `bitorder='big'` ensures that the bits are packed in big-endian order, meaning the most significant bit is first.

5. **Writing to a Binary File**

   After converting sequences to bytes, the next step is to create a binary file and write the necessary data::

      with open(filename, "wb") as binary_file:
          binary_file.write(slen.to_bytes(2, byteorder='big'))  # Write length as 2 bytes
          binary_file.write(pol_bytes)  # Write polarity sequence
          binary_file.write(on_bytes)  # Write ~ON sequence

   The `wb` flag ensures that the file is opened in binary write mode. Note that `slen.to_bytes(2, byteorder='big')` writes the length of the original sequence as 2 bytes.

6. **Debugging and Output**

   To view the byte arrays or for debugging purposes, print the following::

      print(pol_bytes)
      print(on_bytes)
      print(f'Sequence length = {slen}, {slen.to_bytes(2, byteorder="big")})')
      print(f"Pol array = {pol}")
      print(f"ON_ array = {on_}")

   This will display the byte arrays, sequence lengths, and the contents of `pol` and `on_` after padding.
