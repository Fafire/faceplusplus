FacePlusPlus Java SDK
Face++�Ǳ������ӿƼ����޹�˾��Megvii����������Ӿ�����ƽ̨ ּ�ڴ��������ã�����ǿ��ƽ̨���ݵ���һ���Ӿ�����
http://www.faceplusplus.com/

author Nat.Yan 
email:yjy910323@gmail.com
======
Client c = new Client("640cef26df9b65d4fea480215cd51975","iD5K1vGzawH5nss_e2s8oG569ZHrtNd6");
System.out.println("ÿСʱ QUOTA_SEARCH:"+c.getQuotaSearch());
System.out.println("ÿСʱ QUOTA_ALL:"+c.getQuotaAll());
//�������е�group
List<Group> allGroups = c.getAllGroups();
//�������е�Person
List<Person> allPersons = c.getAllPersons();
		
Face f1 = new Face(c, "your_face_id");
Face f2 = new Face(c, "your_face_id");
		
//����һ����ʵ��person by person-id
Person p1 = new Person(c, "your_person_id");
//����һ�������ڵ�Person
Person p2 = new Person(c);
p2.setName("name");//Ϊ�����ڵ�person����name
p2.create();//����person
p2.delete();//ɾ��person
p2.getFaces();//��ȡ����˵�face
p2.addFace(f1);//Ϊ����������һ��face
p2.removeFaec(f1);//Ϊ��������Ƴ�һ��face
		
//ͨ��groupId����һ����ʵ���ڵ�group
Group g1 = new Group(c,"your_group_id",Constants.ID);
//ͨ��groupName����һ����ʵ���ڵ�group
Group g2 = new Group(c,"your_group_name",Constants.NAME);
//����һ�������ڵ�group
Group g3 = new Group(c);
g3.setName("group");//Ϊ�����ڵ�group����name
g3.setTag("tag");//Ϊ�����ڵ�group����tag
g3.create();//����group��
g3.addPerson(p1);
g3.removePerson(p2);
g3.delete();
		
c.detect(new File("your_photo_path"));
c.detect("http_url");
c.compare(f1, f2);
c.recognize(g1, new File("your_photo_path"));
c.search(f1, g3);
c.search(f1, g3, "50");
c.train(g3);