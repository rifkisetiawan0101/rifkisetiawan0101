# GAME DESIGN DOCUMENTATION - TRASH ISSUE
Dokumen berikut ini adalah Game Design Documentation untuk projek game Trash Issue, Top 10 Student Category GAMESEED 2025.

## (3C) CHARACTER, CAMERA, CONTROL

### Character:
- Animation yang dipengaruhi posisi mouse: jika mouse di kanan character, maka animasi CharacterDown dengan flip x | jika mouse di kiri atas player, maka animasi CharacterUp dsb.
- Animation dipisah dalam 3 part: Front, Body, dan Back (Front dan Back adalah kaki)
- Stamina: Energi yang digunakan player untuk melakukan dash. Tidak bisa dash jika stamina kurang. Stamina akan terisi over time

### Camera:
Follow target: Player;

### Control:
- Movement: AWSD
- Dash: Left Shift, Space, Right Mouse; Dash dengan stamina dan diberikan cooldown;
- SwapWeapon: E; SwapWeapon slot dengan keyboard E (Slot 1 > (Key E) > Slot 2 > (Key E) > Slot 1);

### CharacterStats:
- Health (increase MaxHealth by n%)
- MoveSpeed (increase MoveSpeed by n%)
- Attack (increase DamageModifier by n%)
- CritRate (increase CritRate by n%)
- CritDamaege (increase CritDamage by n%)
- FireRate (increase FireRate by n)
- ProjectileSpeed (increase ProjectileSpeed by n%)
- Ammunition (increase Ammunition by n)
- Lifesteal (increase Lifesteal by n%) [Note: Belum masuk ke character stats]
- Stamina (increase Stamina by n) [Note: Belum masuk ke character stats]

## ABILITY CARD (TRASH DROP SILVER)
- Ability Card yang berbeda setiap walkthrough Stage. 
- Player diberikan 3 kartu yang meningkatkan stats dan direset ketika memulai stage baru.

### How to Get:
- Selesaikan satu wave dan Drop sebuah TrashDropSilver (kecuali boss wave). 
- Ketika dicollect dengan hold F, dapatkan 3 dari 8 kartu secara acak. 
- Player tidak memilih, melainkan langsung mendapatkan stats dari ketiganya.

### Ability Card :
Incremental Ability: Ability yang memiliki peningkatan dan dapat muncul beberapa kali. Jika memilih ability yang sama, akan meningkatkan persentase increment;

### Incremental Ability:
- HealthAbility (increase n%)
- MoveSpeedAbility (increase n%)
- AttackAbility (increase n%)
- CritAbility (increase for crit rate n% and crit damage 2n%)
- FireRateAbility (increase n%)
- ProjectileSpeedAbility (increase n%)
- AmmunitionAbility (increase n)
- LifestealAbility (increase n%)
- StaminaAbility (increase n)

## WEAPON CARD (TRASH DROP GOLD)
- Player akan unlock Weapon Card yang berbeda setiap akhir memenangkan Stage. 
- Player diberikan 2 Weapon Card yang akan membuka senjata baru di Lobby Inventory.

### How to Get:
- Selesaikan satu stage dan Drop sebuah TrashDropGold. 
- Ketika dicollect dengan hold F, dapatkan 2 weapon card yang sudah pre-defined. 

## CHOOSE AND SWAP WEAPON
- Player memiliki 3 slot weapon;
- Player dapat memilih dan mengatur senjata untuk slot kedua dan ketiga, sedangkan slot pertama tidak bisa diubah.
- Swap wapon dengan keyboard Q. (Slot 1 > (Key Q) > Slot 2 > (Key Q) > Slot 1);

### Variant Weapons:
NamaWeapon: Projectile; weapon effect descriptions
- BasicWeapon: Tulang Ikan; menembakkan 1 projectile;
- RapidWeapon: Ranting pohon; menembakkan 3 projectile beruntun;
- RicochetWeapon: Tulang ayam; tulang memantul dan mencari musuh terdekat, pantulan sebanyak (n) kali;
- SlowWeapon; Tinta Cumi Hitam; menembakkan 1 projectile AoE, ketika hancur akan memberikan AoE slow effect;
- ElectricBatteryWeapon: Baterai CAB; menembakkan 1 projectile AoE, ketika hancur akan memberikan AoE damage listrik;

Unusable to Player:
- SoundWeapon: Speaker; menembakkan 1 projectile AoE, ketika hancur akan memberikan AoE knockback.

## UNDESTROYABLE OBJECT
Object yang bisa digunakan player sebagai obstacle/wall di dalam map, misalnya berupa pager. Object dengan layer atau Tag Collider. 

## ENEMY
- Enemy berupa dog yang memiliki behaviour masing-masing.
- Berdasarkan type-nya, enemy dibedakan menjadi melee dan range, sama-sama menembakkan senjata, namun melee enemy menggunakan weapon dan projectile null.
- Enemy menerapkan Inheritance Behaviour Pattern, dimana semua enemy menggunakan behaviour BasicDogEnemy untuk tembakan normal (kecuali Wizard dan Necro), dengan beberapa enemy menurunkannya ke pattern masing-masing (contohnya CrazyDog, 

### ENEMY TYPE
NamaEnemy: BasicAbility; SpecialAbility power descriptions;
- BasicDog: Menyerang player menggunakan BasicWeapon; (melee)
- HyperDog: [Include BasicDog]; Mendeteksi projectile dalam sebuah dan melakukan Dash ke arah random dengan cooldown (n) detik; (range)
- InkDog: [Include BasicDog]; Melemparkan SlowWeapon ke arah player dengan cooldown (n) detik; (range)
- NecroDog: [Include BasicDog]; Spawn MinionDog yang akan mati dalam 1 hit dengan cooldown (n) detik. (range)
- MinionDog: [Include BasicDog]; Mati dalam 1 kali hit; (melee)
- TankerDog: [Include BasicDog]; Memiliki ukuran dan Health yang lebih besar; (melee)
- WizardDog: [Include BasicDog]; Memberikan buff effect kepada semua musuh dalam radius (n) dengan cooldown (n) detik. Buff effect berupa increase movement speed sebesar (n)% untuk melee enemy, dan increase fire rate sebesar (n)% untuk range enemy. Buff effect akan hilang jika WizardDog dikalahkan; (range)
- BossElectroDog: [Include BasicDog]; Melemparkan projectile sebanyak (n) dengan arah spread angles dengan cooldown (n) detik.
- BossSoundDog: [Include BasicDog]; Mengeluarkan shockwave yang akan knockback player dengan cooldown (n) detik.

## STAGES
- Stage merupakan arena bermain di game Trash Issue.
- Satu stage terdiri dari banyak waves.
- Jika mengalahkan musuh di semua stage, akan drop TrashDropGold dan menampilkan Result victory;
- Jika kalah di pertengahan stage, akan menampilkan Result lose;

### Stage Tutorial:
Stage 1 yang diperkecil untuk tutorial;

### Stage 1 (Parking Area):
Stage environment di tempat parkir dengan nuansa siang hari.

### Stage 2 (Night Park):
Stage environment di taman tempat konser dengan nuansa malam hari.

## WAVES
- Waves merupakan sekumpulan musuh yang akan dispawn.
- Lebih dari satu waves akan menciptakan stage.
- Di dalam waves terdapat enemy groups berupa mini wave yang dapat dispawn secara burst (sekaligus) maupun trickle (satu per satu).

## STAGES LEVEL DESIGN
Di bawah ini adalah wave data pada setiap stage:
(jumlah) EnemyType; spawn type

### StageTutorial_Wave1
- 3 BasicDogTutorial; burst

### StageTutorial_Wave2
- 5 BasicDogTutorial; burst

### Stage1_Wave1
- 4 BasicDog; burst
- 2 CrazyDog; burst

### Stage1_Wave2
- 5 BasicDog; burst
- 3 CrazyDog; burst
- 2 InkDog; burst

### Stage1_Wave3
- 2 BasicDog; burst
- 5 CrazyDog; burst
- 2 InkDog; burst
- 1 NecroDog; burst

### Stage1_Wave4
- 1 BasicDog, 1 CrazyDog, 1 InkDog, 1 NecroDog; burst
- 1 BossElectroDog; burst
- 1 BasicDog, 1 CrazyDog, 1 InkDog, 1 NecroDog; burst

### Stage1_Wave2
- 1 TankDog; burst
- 2 BasicDog; burst
- 4 CrazyDog; burst
- 2 InkDog; burst

### Stage1_Wave3
- 1 TankDog; burst
- 2 BasicDog; burst
- 4 CrazyDog; burst
- 2 InkDog; burst
- 2 NecroDog; burst

### Stage1_Wave4
- 4 CrazyDog; burst
- 1 InkDog; burst
- 1 WizardDog; burst
- 2 NecroDog; burst
- 2 BossElectroDog Half; burst

### Stage1_Wave5
- 1 TankDog, 2 BasicDog, 2 CrazyDog, 1 InkDog, 1 WizardDog, 1 NecroDog, 1 BossElectroDog Half; burst
- 1 BossSoundDog; burst
- 1 TankDog, 1 BasicDog, 1 CrazyDog, 1 InkDog, 1 WizardDog, 1 NecroDog; burst

## NOTES
(n)% di CharacterStats dan IncrementalAbility akan meningkat 100% per level (misal level 1: 5%, maka level 2: 10%)

## GAME FLOW
### If Doesn't Have Save game:
HomeScreen > (Start) > MainMenu > (Select Stage) > StageScene_1 > (Win or Defeat) > MainMenu
HomeScreen > (Continue) > (Pop Up: You don't have save game fucker)

### If Has Save game:
HomeScreen > (Start) > (Pop Up: Are you sure want to start over?)
HomeScreen > (Continue) > MainMenu



### CUT FEATURE BELOW

```

## CHOOSE ABILITY CARD
Ability Card yang berbeda setiap walkthrough Stage. Player diberikan 4 slot kartu dan direset ketika memulai stage baru.

### How to Get:
Kumpulkan EXP dengan mengalahkan enemy dan naikkan level
Setiap kali menaikkan level akan mendapatkan 3 dari 8 kartu secara acak 

Constant Ability: Ability yang tidak memiliki peningkatan dan hanya muncul sekali;
### Constant Ability:
NamaAbility: Ability effect descriptions;
DoubleWeaponAbility: Memberikan akses untuk menembakkan kedua weapon di slot secara bersamaan.
MagnetAbility: Memberikan efek magnet untuk player mengambil EXP dalam (n) radius.
SpreadProjectileAbility: Ketika projectile player mengenai target akan menyebar ke 6 arah dan memberikan damage masing-masing (n)% dari damage projectile asli.
ShieldAbility: Memberikan shield yang akan menghalau semua projectile selama (n) detik dan memiliki cooldown (n) detik; Shield berotasi mengikuti cursor dan memiliki pivot sama seperti weapon;

## ALLY TYPE
Rekan yang direkrut setiap kali player menyelesaikan 1 stage; Ally akan bertambah 1 setiap clear stage;
NamaAlly: BasicAbility; SpecialAbility power descriptions;
BlackCat: Menyerang player menggunakan BasicWeapon; Melemparkan SlowWeapon ke arah enemy dengan cooldown (n) detik. Tidak bisa diserang enemy;

## SKILL POINT ALLOCATION
Player merndapatkan 1 SkillPoint setiap kali menaikkan level di InGame stage
CharacterStats dapat ditingkatkan dengan SkillPoint.
SP dapat dialokasikan dengan menambah atau mengurangi level stats selama SP masih mencukupi. 
Jumlah SP yang bisa didapatkan dibatasi sesuai jumlah stage clear 

### SP Limitting:
0 stage clear: (n) SP
1 stage clear: (n) SP

## DESTROYABLE CRATES
Item yang bisa dihancurkan untuk mengeluarkan battle effect

### Variant Crates:
NamaCrate: Item; Crate effect descriptions
BinCrate: Tong Sampah: Spread kaleng makanan anjing; Memancing musuh ke kaleng selama (n) detik.
CardboardCrate: Drop EXP sebanyak (n)

```
