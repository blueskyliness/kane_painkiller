
<h1 align="center">Advanced Medical System [ESX]</h1>

<p align="center">
  <strong>สคริปต์ระบบการแพทย์ขั้นสูงสำหรับ ESX Framework ที่มาพร้อมระบบ Painkiller & AED ที่ปลอดภัยและปรับแต่งง่าย</strong>
</p>

<p align="center">
    <img src="https://img.shields.io/badge/Framework-ESX-red?style=for-the-badge&logo=lua" alt="Framework: ESX">
    <img src="https://img.shields.io/badge/Version-1.1.1-blue?style=for-the-badge" alt="Version">
    <img src="https://img.shields.io/badge/Status-Stable-brightgreen?style=for-the-badge" alt="Status: Stable">
    <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" alt="License: MIT">
</p>

<p align="center">
  <a href="#-ภาษาไทย">🇹🇭 ภาษาไทย</a>
  &nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#-english">🇬🇧 English</a>
</p>

---

## 🇹🇭 ภาษาไทย

### 📜 สารบัญ
* [✨ คุณสมบัติเด่น](#-คุณสมบัติเด่น)
* [🎬 ตัวอย่างการใช้งาน](#-ตัวอย่างการใช้งาน)
* [📦 สิ่งที่ต้องมี (Dependencies)](#-สิ่งที่ต้องมี-dependencies)
* [🛠️ การติดตั้ง](#-การติดตั้ง)
* [🔧 การตั้งค่า](#-การตั้งค่า)
* [💾 การเพิ่มไอเทมในฐานข้อมูล](#-การเพิ่มไอเทมในฐานข้อมูล)

---

### ✨ คุณสมบัติเด่น

- **💊 ระบบฟื้นฟูพลังชีวิต:** ใช้ยาแก้ปวดเพื่อเพิ่มเลือดตามที่กำหนด
- **⚡️ ระบบชุบชีวิต:** ใช้เครื่อง AED เพื่อชุบชีวิตผู้เล่นอื่นที่อยู่ในสถานะโคม่า
- **🎬 อนิเมชันและ UI สมจริง:** มาพร้อมอนิเมชันและแถบความคืบหน้าขณะใช้งาน
- **👮‍♂️ จำกัดการใช้งานตามอาชีพ:** กำหนดไอเทมให้ใช้ได้เฉพาะอาชีพที่กำหนด
- **⚔️ ระบบ Warzone:** ตั้งค่าไอเทมให้ใช้ได้เฉพาะในพื้นที่ที่กำหนด
- **⏱️ ระบบคูลดาวน์:** ป้องกันการใช้ไอเทมรัวๆ ด้วยระบบหน่วงเวลา
- **🛡️ ปลอดภัยสูง:** ตรวจสอบข้อมูลฝั่งเซิร์ฟเวอร์อย่างรัดกุมเพื่อป้องกันการโกง
- **⚙️ ปรับแต่งง่าย:** ตั้งค่าทุกอย่างได้ละเอียดในไฟล์ `config.lua`
- **🚀 ประสิทธิภาพสูง:** เขียนโค้ดมาอย่างดี กินทรัพยากรน้อย

### 🎬 ตัวอย่างการใช้งาน

<p align="center">
  <i>(แนะนำให้ใส่ภาพ GIF หรือวิดีโอแสดงการทำงานของสคริปต์ที่นี่)</i><br>
  <img src="https://via.placeholder.com/600x300.png?text=Script+Preview+GIF" alt="Script Preview">
</p>

### 📦 สิ่งที่ต้องมี (Dependencies)

| ทรัพยากร (Resource)                                       | เหตุผล                               |
| --------------------------------------------------------- | ------------------------------------ |
| [`es_extended`](https://github.com/esx-framework/esx-legacy) | เป็น Core Framework หลักของเซิร์ฟเวอร์ |
| [`mythic_progbar`](https://github.com/mythicrp/mythic_progbar) | สำหรับแสดงแถบความคืบหน้า            |
| [`mythic_notify`](https://github.com/mythicrp/mythic_notify)  | สำหรับแสดงการแจ้งเตือน               |


### 🛠️ การติดตั้ง

1.  ดาวน์โหลดไฟล์สคริปต์และนำไปไว้ในโฟลเดอร์ `resources`
2.  เพิ่มโค้ดต่อไปนี้ลงในไฟล์ `server.cfg` **(สำคัญ: ต้องอยู่หลัง Dependencies)**
    ```cfg
    ensure es_extended
    ensure mythic_progbar
    ensure mythic_notify

    ensure kane_painkiller # <-- แก้เป็นชื่อโฟลเดอร์ของคุณ
    ```
3.  ไปที่หัวข้อ [การเพิ่มไอเทมในฐานข้อมูล](#-การเพิ่มไอเทมในฐานข้อมูล) เพื่อเพิ่มไอเทมลงใน Database

### 🔧 การตั้งค่า

การตั้งค่าหลักทั้งหมดอยู่ใน `config.lua` คุณสามารถปรับแต่งการทำงานของไอเทมแต่ละชิ้นได้อย่างอิสระ

<details>
<summary><strong>💊 คลิกเพื่อดูตัวอย่างการตั้งค่าไอเทมทั่วไป</strong></summary>

```lua
-- ใน Config.GeneralItems
["painkiller"] = {
    healAmount = 40,         -- ปริมาณเลือดที่ฟื้นฟู
    cooldown = 3,            -- คูลดาวน์ (วินาที)
    maxHealth = 200,         -- เลือดสูงสุดที่ไอเทมนี้จะฮีลถึง
    requiresAlive = true,    -- ต้องมีชีวิตอยู่ถึงจะใช้ได้
    animation = { 
        dict = 'anim@heists@narcotics@funding@gang_idle', 
        name = 'gang_chatting_idle01', 
        duration = 3000      -- ระยะเวลา (milliseconds)
    }
},
```
</details>

<details>
<summary><strong>👮‍♂️ คลิกเพื่อดูตัวอย่างการตั้งค่าไอเทมจำกัดอาชีพ</strong></summary>

```lua
-- ใน Config.JobRestrictedItems
["aed_p"] = {
    allowedJobs = { "police", "ambulance" }, -- อาชีพที่ได้รับอนุญาต
    type = "revive",
    cooldown = 20,
    requiresAlive = true,
    maxDistance = 1.5, -- ระยะห่างสูงสุดในการชุบ
    animation = { 
        dict = "mini@cpr@char_a@cpr_str", 
        name = "cpr_pumpchest", 
        duration = 12000
    }
},
```
</details>

<details>
<summary><strong>⚔️ คลิกเพื่อดูตัวอย่างการตั้งค่า Warzone</strong></summary>

```lua
-- ใน Config.UseZone
{ x = 3862.16, y = -1656.37, z = 627.75, r = 150.52 }, -- Warzone 1
-- เพิ่มโซนอื่นๆ ต่อที่นี่ได้เลย
```
</details>

### 💾 การเพิ่มไอเทมในฐานข้อมูล

> **สำคัญ:** คุณต้องเพิ่มไอเทมเหล่านี้ลงในตาราง `items` ในฐานข้อมูลของคุณเพื่อให้ ESX รู้จักและใช้งานได้

```sql
INSERT INTO `items` (`name`, `label`, `weight`) VALUES
	('painkiller', 'Painkiller', 1),
	('aed', 'AED', 5),
    ('painkiller_wz', 'WZ Painkiller', 1),
    ('aed_wz', 'WZ AED', 5),
    ('aed_p', 'Police AED', 5),
    ('painkiller_p', 'Police Painkiller', 1)
;
```

---
---

## 🇬🇧 English

### 📜 Table of Contents
* [✨ Features](#-features)
* [🎬 Showcase](#-showcase)
* [📦 Dependencies](#-dependencies)
* [🛠️ Installation](#-installation)
* [🔧 Configuration](#-configuration)
* [💾 Database Setup](#-database-setup)

---

### ✨ Features

- **💊 Healing System:** Use painkillers to restore health.
- **⚡️ Revive System:** Use an AED to revive other players.
- **🎬 Immersive UI/Animations:** Comes with animations and progress bars for realism.
- **👮‍♂️ Job Restrictions:** Restrict item usage to specific jobs.
- **⚔️ Warzone System:** Set items to be usable only in designated zones.
- **⏱️ Cooldown System:** Prevents item spamming with a cooldown timer.
- **🛡️ High Security:** Robust server-side validation to prevent exploits.
- **⚙️ Highly Configurable:** Configure everything in detail via `config.lua`.
- **🚀 High Performance:** Well-optimized code with low resource consumption.

### 🎬 Showcase

<p align="center">
  <i>(It's recommended to add a GIF or video of the script in action here.)</i><br>
  <img src="https://via.placeholder.com/600x300.png?text=Script+Preview+GIF" alt="Script Preview">
</p>

### 📦 Dependencies

| Resource                                                  | Reason                               |
| --------------------------------------------------------- | ------------------------------------ |
| [`es_extended`](https://github.com/esx-framework/esx-legacy) | Main server Core Framework           |
| [`mythic_progbar`](https://github.com/mythicrp/mythic_progbar) | To display the progress bar          |
| [`mythic_notify`](https://github.com/mythicrp/mythic_notify)  | To display notifications             |

### 🛠️ Installation

1.  Download the script and place it in your `resources` directory.
2.  Add the following line to your `server.cfg` **(Important: must be after the dependencies)**.
    ```cfg
    ensure es_extended
    ensure mythic_progbar
    ensure mythic_notify

    ensure kane_painkiller # <-- Change to your folder name
    ```
3.  Proceed to the [Database Setup](#-database-setup) section to add the items to your database.

### 🔧 Configuration

All primary settings are in `config.lua`. You can freely customize the behavior of each item.

<details>
<summary><strong>💊 Click to see General Item Config Example</strong></summary>

```lua
-- In Config.GeneralItems
["painkiller"] = {
    healAmount = 40,
    cooldown = 3,
    maxHealth = 200,
    requiresAlive = true,
    animation = { 
        dict = 'anim@heists@narcotics@funding@gang_idle', 
        name = 'gang_chatting_idle01', 
        duration = 3000
    }
},
```
</details>

<details>
<summary><strong>👮‍♂️ Click to see Job-Restricted Item Config Example</strong></summary>

```lua
-- In Config.JobRestrictedItems
["aed_p"] = {
    allowedJobs = { "police", "ambulance" }, -- Whitelisted jobs
    type = "revive",
    cooldown = 20,
    requiresAlive = true,
    maxDistance = 1.5, -- Max revive distance
    animation = { 
        dict = "mini@cpr@char_a@cpr_str", 
        name = "cpr_pumpchest", 
        duration = 12000 
    }
},
```
</details>

<details>
<summary><strong>⚔️ Click to see Warzone Config Example</strong></summary>

```lua
-- In Config.UseZone
{ x = 3862.16, y = -1656.37, z = 627.75, r = 150.52 }, -- Warzone 1
-- Add more zones here
```
</details>

### 💾 Database Setup

> **Important:** You must add these items to your `items` table in your database for ESX to recognize them.

```sql
INSERT INTO `items` (`name`, `label`, `weight`) VALUES
	('painkiller', 'Painkiller', 1),
	('aed', 'AED', 5),
    ('painkiller_wz', 'WZ Painkiller', 1),
    ('aed_wz', 'WZ AED', 5),
    ('aed_p', 'Police AED', 5),
    ('painkiller_p', 'Police Painkiller', 1)
;
```
