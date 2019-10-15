###图片移位
cv2.warpAffine(src, M, dsize[, dst[, flags[, borderMode[, borderValue]]]]) → dst

src - 输入图像
M - 变换矩阵：作为仿射变换矩阵，一般反映平移或旋转的关系
dsize - 输出图像的大小
flag - 插值方法的组合

###生成仿射变换矩阵：cv2.getAffineTransform(InputArray src, InputArray dst)
InputArray src：表示输入的三个点
InputArray dst:表示输出的三个点

 
```
#src 3点->dst 3点 (每个点的先后顺序无明确规定，但是两矩阵对应点相互对应)
matSrc = np.float32([[0,0],[height-1,0],[0,width-1]])
matDst = np.float32([[50,50],[300,height-200],[width-300,100]])
matscale = cv2.getAffineTransform(matSrc,matDst)
dst = cv2.warpAffine(img,matscale,(width,height))
```

###图片的叠加以及透明度设置cv2.addWeighted(src1, alpha, src2, beta, gamma[, dst[, dtype]])
其中alpha为src1的透明度，beta为src2的透明度
