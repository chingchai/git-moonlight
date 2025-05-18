# 👩‍💻 Contributing Guide

ยินดีต้อนรับสู่โปรเจกต์ของเรา! กรุณาอ่านแนวทางด้านล่างก่อนเริ่มต้นการ contribute หรือสร้าง pull request.

---

## ✅ Workflow Overview

1. **Fork และ Clone**
2. **สร้าง Branch ใหม่ จาก `develop`**
3. **ตั้งชื่อ Branch ตามรูปแบบที่กำหนด**
4. **Commit อย่างมีความหมาย**
5. **Push และสร้าง Pull Request มาที่ `develop`**
6. **รอ Review และ Approve**

```
Backlog → Ready → In Progress → In Review (QA) → Testing → Ready to Deploy → Done
                           ↖------------------------↙
                   (Testing Failed → กลับ In Progress)
```

---

## 🌿 Branch Naming Guidelines

| ประเภทงาน     | Prefix     | ตัวอย่าง Branch                        |
|----------------|------------|----------------------------------------|
| ฟีเจอร์ใหม่    | `feature/` | `feature/123-user-login`              |
| แก้บั๊กทั่วไป  | `bugfix/`  | `bugfix/234-invalid-date-format`     |
| แก้บั๊กด่วน    | `hotfix/`  | `hotfix/2025-05-17-fix-prod-crash`   |
| เตรียมปล่อยเวอร์ชัน | `release/` | `release/2025-05-31` or `release/1.2.0` or `release/sprint-22`|
| งานอื่นๆ (CI, config ฯลฯ) | `chore/`   | `chore/update-lint-config`           |
| ปรับโครงสร้าง | `refactor/`| `refactor/clean-user-service`        |
| แก้เอกสาร     | `docs/`    | `docs/update-api-docs`               |

> 💡 *หมายเหตุ*: ถ้ามี Issue ID ให้ใส่ไว้ด้วย เช่น `feature/456-new-dashboard`


### 🌱 **Branch Types**

1. **🧩 Feature Branch (`feature/*`)**  
   ใช้สำหรับการพัฒนาฟีเจอร์ใหม่  
   **Naming convention**: `feature/{issue-id}-{short-description}`  

   **ตัวอย่าง**:
   - `feature/123-add-user-login`
   - `feature/456-add-search-functionality`

2. **🛠 Bugfix Branch (`bugfix/*`)**  
   ใช้สำหรับแก้ไขบั๊กที่ยังไม่ได้ไปที่ Production  
   **Naming convention**: `bugfix/{issue-id}-{short-description}`  

   **ตัวอย่าง**:
   - `bugfix/234-fix-login-error`
   - `bugfix/275-fix-signup-validation`

3. **🔥 Hotfix Branch (`hotfix/*`)**  
   ใช้สำหรับแก้ไขปัญหาด่วนที่เกิดใน Production  
   **Naming convention**: `hotfix/{yyyy-mm-dd}-{short-description}` หรือ `hotfix/{issue-id}-{short-description}`  

   **ตัวอย่าง**:
   - `hotfix/2025-05-17-fix-crash`
   - `hotfix/302-fix-prod-payment-bug`

4. **🎯 Release Branch (`release/*`)**  
   ใช้สำหรับเตรียมการปล่อย version ใหม่  
   **Naming convention**: `release/{version}` หรือ `release/{yyyy-mm-dd}`  

   **ตัวอย่าง**:
   - `release/1.0.0`
   - `release/2025-05-31`

5. **🧹 Chore (`chore/*`)**    
   ใช้สำหรับงานจิปาถะ เช่น config, CI/CD  
   **Naming convention**: `chore/{short-description}` 

   **ตัวอย่าง**:
   - `chore/setup-eslint`
   - `chore/update-ci-yml`
     
6. **📦 Refactor (`refactor/*`)**    
   ใช้สำหรับปรับโครงสร้างโค้ด 
   **Naming convention**: `chore/{short-description}` 

   **ตัวอย่าง**:
   - `refactor/simplify-user-service`
   - `refactor/clean-db-calls`

7. **📚 Docs (`docs/*`)**    
   ใช้สำหรับเอกสาร
   **Naming convention**: `chore/{short-description}` 

   **ตัวอย่าง**:
   - `docs/update-readme`
   - `docs/api-doc-v1`

### 💡 **Best Practices**
- ใช้ ตัวอักษรเล็กทั้งหมด **lowercase**  ในการตั้งชื่อ branch
- **ใช้ `-` แทนการเว้นวรรค** เช่น `feature/123-add-user-login`
- **ไม่ใช้เว้นวรรค หรือ `_ (underscore)` เด็ดขาด**
- **เก็บคำสั้นๆ ที่อธิบายฟีเจอร์** ใน `slug-description`
- ถ้ามี **issue ID ให้ใส่ด้านหน้า** เช่น `feature/234-...`
- ใช้ **ตัวเลขวัน** หรือ **issue ID** ในการตั้งชื่อ `hotfix` เพื่อการตรวจสอบง่ายขึ้น
- **หลีกเลี่ยงการใช้ชื่อ branch ที่เป็น general term** เช่น `feature/test`, `feature/new-feature` เพราะมันไม่บ่งบอกถึงงานที่ทำ


---

## ✍️ Commit Message Guidelines

ใช้รูปแบบ Commit Message ดังนี้:

**Structure**:  
  `TYPE(scope): message`  
  Example: `feat(auth): add login functionality`

**Examples**:
- `feat(auth): add login endpoint`
- `fix(api): correct date parsing issue`
- `docs(readme): update contributing guidelines`

**Types**:
- `feat`: New feature เพิ่มฟีเจอร์
- `fix`: Bug fix แก้บั๊ก
- `docs`: เอกสาร 
- `style`: เรื่อง style (ไม่มี logic เปลี่ยน)
- `refactor`: ปรับปรุงโค้ด
- `test`: เพิ่ม/ปรับเทส
- `chore`: งานจิปาถะ (e.g., build, deployment)

---

## 🧪 Testing Before PR

- ทดสอบให้แน่ใจว่าไม่มีบั๊กใน Unit / Integration Test
- ผ่าน QA checklist (ถ้ามี)

---

## 📦 Pull Request

- ตั้งชื่อ PR ให้อ่านเข้าใจง่าย เช่น: `เพิ่มหน้า Dashboard และแก้ไข API login`
- ระบุคำอธิบายที่ชัดเจนเกี่ยวกับสิ่งที่คุณได้ทำ
- เชื่อมโยงกับ Issue ด้วยคำสั่ง:  
  `Closes #123` หรือ `Fixes #234`
- เพิ่มป้ายกำกับที่เกี่ยวข้อง (e.g., `bug`, `feature`, `enhancement`).
- Ensure all tests pass before merging.



---













