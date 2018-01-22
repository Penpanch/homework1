# git commit
### เป็นการ commit ด้วยคำสั่ง git commit -m "YOUR MESSAGE" ดังนี้

git commit -m "add sample index page"

[master (root-commit) 2a33074] add sample index page
 1 file changed, 10 insertions(+)
 create mode 100644 index.html
git commit คือการสร้าง snapshot ให้กับ repository ทำให้เราสามารถย้อนกลับมาดูว่าเราเปลี่ยนหรือแก้ไขโค๊ดอะไรไปบ้างได้

เกี่ยวกับการใช้งาน git add เราสามารถ add ที่ละหลายๆไฟล์ด้วยการใช้ * ก็ได้ เช่น

git add . : add ไฟล์ทั้งหมด
git add '*.txt' : add ไฟล์ทั้งหมดที่นามสกุล .txt เป็นต้น
git log
เราสามารถตรวจสอบดูได้ว่าเราทำอะไร git ไปแล้วบ้าง ด้วยการใช้คำสั่ง

git log
ต่อมาผมทำการสร้างไฟล์เปล่าๆ ขึ้นมาอีก 2 ไฟล์คือ about.html และ contact.html จากนั้นลองเช็คสถานะด้วย git status อีกครั้ง จะได้ดังภาพ

On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)

    about.html
    contact.html

nothing added to commit but untracked files present (use "git add" to track)
สิ่งที่เราต้องทำก็คือ ทำการ git add เพื่อให้ไปอยู่ใน staged และพร้อมที่จะ commit ก็เริ่มเลย

git add about.html contact.html
git commit -m "add empty about and contact page"
ลองนึกถึง หากตอนนี้ถ้าเป็นโปรเจ็คจริงๆ แล้วเราเผลอลบไฟล์ไปจะทำยังไง ? Git ช่วยได้ครับ ตอนนี้สมมติ ลองลบไฟล์ index.html ทิ้งดูครับ แล้วลอง git status ดูว่าเป็นยังไง

On branch master
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

    deleted:    index.html

no changes added to commit (use "git add" and/or "git commit -a")
Git ก็รู้ทันทีว่าไฟล์ของเราถูกลบออกไปแล้ว แต่ Git มัน track ไว้ให้ และลองใช้อีกคำสั่งครับ นั่นก็คือ

git diff
git diff HEAD
เอาไว้เช็คว่ามีอะไรเปลี่ยนแปลงบ้าง จากข้อความด้านล่าง โค๊ดสีแดงคือโค๊ดที่ลบ ถ้ามีสีเขียวแสดงว่าเป็นโค๊ดที่ถูกเพิ่ม

diff --git a/index.html b/index.html
deleted file mode 100644
index 144f699..0000000
--- a/index.html
+++ /dev/null
@@ -1,10 +0,0 @@
-<!DOCTYPE html>
-<html lang="en">
-<head>
-       <meta charset="UTF-8">
-       <title>Introduction to Git and Github by DevAhoy</title>
-</head>
-<body>
-       <h1>Hello World</h1>
-</body>
-</html>
\ No newline at end of file
git reset
ทีนี้อยากจะ reset กู้คืนไฟล์ที่เผลอลบไป เช่น เผลอลบ index.html ก็เพียงแค่ใช้คำสั่ง

git checkout index.html
แต่ถ้าเราดันเผลอลบ แล้วก็ยังไป add เข้าสู่ staged แล้ว ก็ต้องใช้

git reset index.html
แล้วถ้าเราดันไป commit มันซะแล้ว วิธีที่จะย้อนกลับไป commit ล่าสุดก็คือ

git reset --soft HEAD~1
ส่วนถ้าเราใช้คำสั่งนี้ จะเป็นการลบไฟล์ index.html ออกจากการ track ของ Git แต่ไม่ได้ลบไฟล์ในโปรเจ็คของเรา

git remove --cached index.html
Git branch
ต่อมาเป็นการพูดถึง git branch เป็น feature ที่ช่วยให้นักพัฒนาสามารถที่จะทำงานได้สะดวกขึ้น ยกตัวอย่างเช่น เรามีโค๊ดที่ดีอยู่แล้ว แต่อยากจะทดลองอะไรนิดๆหน่อย หรือแก้ไขอะไรก็ตาม ไม่ให้กระทบกับตัวงานหลัก ก็เพียงแค่สร้าง branch ใหม่ขึ้นมา เมื่อแก้ไขหรือทำอะไรเสร็จแล้ว ก็ค่อยเซฟกลับมาที่ master เหมือนเดิม

วิธีการสร้าง branch ใหม่ จะใช้คำสั่ง

git branch create_new_page
ลองดูรายชื่อ branch ทั้งหมดที่เรามี ดังนี้

git branch

* master
  create_new_page
ตอนนี้เรามี 2 branch อยู่ในเครื่อง วิธีการสลับ branch เราจะใช้ git checkout

git checkout
git checkout branch_name เอาไว้สำหรับเปลี่ยน branch ตัวอย่างเช่น git branch create_new_page ย้าย branch ไปยัง create_new_page

เราสามารถสั่ง git checkout -b create_new_page แบบสั้นๆได้ เป็นการสร้าง branch ใหม่และ checkout ให้เลย เป็นการรวมสองคำสั่งเป็นคำสั่งเดียว นั่นเอง

ใน branch create_new_page ผมเพิ่มไฟล์มาสองไฟล์ service.html และ portfolio.html จะเห็นว่าไฟล์ในโฟลเดอร์จะเป็นแบบนี้

create_new_page branch

จากนั้นทำการ commit ไฟล์ที่เพิ่มลงไปใหม่

git add '*.txt'
git commit -m "I just added new two pages on create_new_page branch"
แล้วลองย้อนกลับไป brach master ด้วย git checkout master ไฟล์ในโฟลเดอร์จะไม่มี service.html และ portfolio.html เนื่องจากเราไม่ได้สร้างที่ brach master นั่นเอง

master branch

git merge
ทีนี้สมมติว่าเรา ทดลองทำ feature อะไรใหม่ๆ แล้วคิดว่ามันดีแล้ว อยากเอามารวมกับ master เราก็ใช้คำสั่ง git merge โดยตัวอย่าง ผมสร้างไฟล์ service.html และ portfolio.html ที่ branch create_new_page และจะนำมารวมกับ master ก็เพียงแค่ใช้:

git checkout master
git merge create_new_page
เริ่มต้นด้วยการ ไปที่ branch หลัก (master)
จากนั้นก็สั่ง git merge branch_name จาก branch ที่ต้องการ มาที่ master
Updating 9d0d9f8..4f176d9
Fast-forward
 portfolio.html | 0
 service.html   | 0
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 portfolio.html
 create mode 100644 service.html
จะเห็นว่าตอนนี้ brach master มีไฟล์ 2 ไฟล์ที่เพิ่มเข้ามาใหม่ พร้อมกับ commit message ที่เคย commit ไว้ก็จะถูกรวมมาอยู่ใน master หมด ทีนี้เมื่อเราทำ feature อะไรเสร็จแล้ว brach create_new_page ก็ไม่ต้องการละ สามารถลบ branch ได้ด้วยคำสั่ง

git branch -d branch_name
git branch -d create_new_page
สำหรับ Git เบื้องต้นในส่วนของ local ก็หมดเพียงเท่านี้ครับ ต่อไปจะเป็น Git บน Server 
