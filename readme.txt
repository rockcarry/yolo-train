# ���� conv �ļ�
./darknet partial yolo-fastest.cfg yolo-fastest.weights yolo-fastest.conv.109 109

# ��ʼѵ��
./darknet detector train voc.data yolo-fastest.cfg yolo-fastest.conv.109

# �Ӷϵ�����ѵ��
./darknet detector train voc.data yolo-fastest.cfg backup/yolo-fastest_last.weights

# ����
./darknet detector test voc.data yolo-fastest.cfg yolo-fastest.weights person.jpg
./darknet detector test voc.data yolo-fastest.cfg yolo-fastest.weights cat.jpg
./darknet detector test voc.data yolo-fastest.cfg yolo-fastest.weights dog.jpg

