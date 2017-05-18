# edgmapping
edgmapping(Elevation Difference Grid Mapping)は,  
高低差格子地図生成のためのFastSLAM 1.0です.

人が生活している屋外環境を対象に,   
3D LIDARのスキャンとジャイロオドメトリなどのデッドレコニングを用いて,  
FastSLAMで高低差格子地図を生成します.  

この手法はROSのnodeとして実装されています.

現在開発中のため, バグが残っているかも知れません.  
また, パラメータ調整も完了していません.  
ですが, 取り敢えず動きます.  

動かす際には,   
<https://github.com/iou16/elevation_difference_cloud_pub>  
<https://github.com/open-rdc/orne_navigation>  
等が必要です.
