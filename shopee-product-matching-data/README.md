# Data Folder

This folder contains instructions and information about the dataset used for the **Multimodal Semantic Search Engine** project.

---

## Dataset

We use the **Shopee Product Matching dataset**, which provides:

- Product images from e-commerce listings
- CSV files with product IDs and labels
- Suitable for **image-to-image similarity** and **product matching tasks**

**Dataset URL:** [Shopee Product Matching on Kaggle](https://www.kaggle.com/competitions/shopee-product-matching/data)

---

## How to Prepare the Data

1. **Download the dataset** from the Kaggle link above.  
2. Place training images in `data/train_images/` and test images in `data/test_images/`.  
3. Save the CSV files in `data/` as shown above.  
4. Ensure filenames in the CSV match the image filenames exactly.

---

## Notes

- For development or demos, you can use a **subset of images** (e.g., 5,000–10,000) to speed up embedding generation.  
- This dataset is **for research purposes** only check the Kaggle competition rules before redistributing any images.  

