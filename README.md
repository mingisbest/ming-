# ming-

# Outlier detection
import numpy as np

def detect_outliers2(df):
    outlier_indices = []

    # 1st quartile (25%)
    Q1 = np.percentile(df, 25)
    # 3rd quartile (75%)
    Q3 = np.percentile(df, 75)
    # Interquartile range (IQR)
    IQR = Q3 - Q1

    # outlier step
    outlier_step = 1.5 * IQR
    for nu in df:
        if (nu < Q1 - outlier_step) | (nu > Q3 + outlier_step):
            df.remove(nu)
    return df

if __name__ == '__main__':
    df = [-3331,2,3,4,11111]
    Outliers_to_drop = detect_outliers2(df)
    # Drop outliers
    print(Outliers_to_drop)
