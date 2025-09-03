import os
import re
from PyPDF2 import PdfMerger

def numerical_sort(value):
    """Extracts numbers from filenames like 'ch 1.pdf' for correct sorting."""
    numbers = re.findall(r'\d+', value)
    return int(numbers[0]) if numbers else float('inf')

def merge_pdfs_from_folder(folder_path, output_file):
    merger = PdfMerger()
    
    # Collect all PDFs in the folder
    pdf_files = [f for f in os.listdir(folder_path) if f.endswith(".pdf")]
    
    # Sort using numerical order (based on chapter numbers)
    pdf_files.sort(key=numerical_sort)
    
    for pdf in pdf_files:
        file_path = os.path.join(folder_path, pdf)
        merger.append(file_path)
        print(f"Added: {pdf}")
    
    merger.write(output_file)
    merger.close()
    print(f"\n✅ Merged {len(pdf_files)} PDFs into {output_file}")

if __name__ == "__main__":
    folder = "/Users/manish/Downloads/database"
    output = "/Users/manish/Downloads/database/database.pdf"
    merge_pdfs_from_folder(folder, output)
