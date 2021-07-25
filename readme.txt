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

