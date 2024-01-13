# SQL-SERVER

## เตือนความจำ
### วิธีตั้งค่า แก้ไข Design ไม่ได้ คลิก
```sql
- Tools
- options
- Designers
- Prevent saving changes that require table re-creation คิ้กออก
```

## ดึงข้อมูลจาก Server นึงไปอีก Server
```sql
-- เช็คเมื่อ Server CS_MASTER มีข้อมูลให้ลบออกก่อน
USE CS_MASTER;
IF EXISTS (SELECT 1 FROM TBL_PACKING_SCAN_BOX WHERE SUBJOB = 'C66/0145-002')
BEGIN
    DELETE FROM TBL_PACKING_SCAN_BOX WHERE SUBJOB = 'C66/0145-002';
END;

-- Insert data from CS_MASTER_TEST
INSERT INTO CS_MASTER.dbo.TBL_PACKING_SCAN_BOX (column1, column2, ...)
SELECT column1, column2, ...
FROM CS_MASTER_TEST.dbo.TBL_PACKING_SCAN_BOX
WHERE SUBJOB = 'C66/0145-002';

```


