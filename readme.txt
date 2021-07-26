# 生成 conv 文件
./darknet partial yolo-fastest.cfg yolo-fastest.weights yolo-fastest.conv.109 109

# 开始训练
./darknet detector train voc.data yolo-fastest.cfg yolo-fastest.conv.109

# 从断点重新训练
./darknet detector train voc.data yolo-fastest.cfg backup/yolo-fastest_last.weights

# 测试
./darknet detector test voc.data yolo-fastest.cfg yolo-fastest.weights person.jpg
./darknet detector test voc.data yolo-fastest.cfg yolo-fastest.weights cat.jpg
./darknet detector test voc.data yolo-fastest.cfg yolo-fastest.weights dog.jpg

# 计算 mAP
./darknet detector map voc.data yolo-fastest.cfg backup/yolo-fastest_last.weights


什么时候停止训练?
一般来说每个类迭代 2000 就足够了，但是总的迭代次数不应少于 4000 次。

当看到 average loss 0.xxxxxx 在多个 iterations 中都不再减小时，你就应该停止训练。avgerage loss 最终一般在 0.05（小模型，简单数据集）到 3.0（大模型，复杂数据集）之间

训练停止之后，你应该从 backup 中选择表现最好的 weight 文件，选择 mAP 或者 IoU 最高的

