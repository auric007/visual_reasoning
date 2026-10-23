# C1 radar and missile error IDs — saved reference

Author: Codex. Human companion: [error_ids.md](error_ids.md).

Task RN-20261023-c1-full-stage1-eval; snapshot 2026-10-23T17:24:07.022965+05:30. Same experiment09 outputs, not a new run. Sources: [error_review](/sfs/vlm_qwen/experiments/2026-10-19/09_c1_full_stage1_eval/reports/error_review/README.md). Radar visualization only; missile cases are IDs-only. Full source CSV files contain images, original model text and Stage1 scores. These are detector-proposal IDs, not an official annotation-registry namespace.

## Radar misclassification IDs

Completed C1 full clean Stage1 benchmark:confidence ≥0.50, polygon IoU ≥0.50. IDs identify detector proposals, not a newly assigned GT instance namespace. Full scene plus ID disambiguates source proposals. No new inference.

Other uses the historical non-target taxonomy, including radome; background means annotation-unmatched, not guaranteed empty. GT index is zero-based in the frozen parsed GT array. Model answer is class-only, with no rationale/confidence. Stage1 confidence belongs to the detector.

Unique errors in this ledger: **262**. Radar and missile ledgers overlap on the30 radar↔missile confusions; do not add them as independent errors.

### missile → radar: 6

| Instance ID | Split | Scene | Raw GT class | GT index (0-based) | Model answer |
|---|---|---|---|---:|---|
| `19DEC21034_0000` | Test1 | `19DEC21034631-S3DS-200013276864_01_P001` | missile | 3 | radar |
| `19MAR13040_0001` | Test1 | `19MAR13040701-S3DS-200013268578_01_P001` | missile | 2 | radar |
| `21DEC27025_0022` | Test1 | `21DEC27025021-S3DS-200012895048_01_P001` | missile | 17 | radar |
| `21FEB15025_0004` | Test1 | `21FEB15025428-S3DS-200011883412_01_P001` | missile | 3 | radar |
| `20SEP27061_0005` | Test2 | `20SEP27061806-S3DS-200011619312_01_P001` | missile | 2 | radar |
| `23MAY19062_0035` | Test2 | `23MAY19062258-S3DS-200011619589_01_P001` | missile | 0 | radar |

### other → radar: 120

| Instance ID | Split | Scene | Raw GT class | GT index (0-based) | Model answer |
|---|---|---|---|---:|---|
| `18MAR10025_0016` | Test1 | `18MAR10025634-S3DS-200012866237_01_P001` | vehicle | 11 | radar |
| `19MAR13040_0000` | Test1 | `19MAR13040701-S3DS-200013268578_01_P001` | vehicle | 9 | radar |
| `19MAR13040_0004` | Test1 | `19MAR13040701-S3DS-200013268578_01_P001` | vehicle | 7 | radar |
| `19MAY10032_0001` | Test1 | `19MAY10032935-S3DS-200012352046_01_P001` | logistic | 1 | radar |
| `19MAY10032_0004` | Test1 | `19MAY10032935-S3DS-200012352046_01_P001` | vehicle | 50 | radar |
| `19SEP16023_0001` | Test1 | `19SEP16023725-S3DS-200011883557_01_P001` | vehicle | 5 | radar |
| `19SEP16023_0026` | Test1 | `19SEP16023725-S3DS-200011883557_01_P001` | vehicle | 81 | radar |
| `19SEP16023_0050` | Test1 | `19SEP16023725-S3DS-200011883557_01_P001` | vehicle | 17 | radar |
| `19SEP16023_0052` | Test1 | `19SEP16023725-S3DS-200011883557_01_P001` | vehicle | 110 | radar |
| `20SEP09053_0011` | Test1 | `20SEP09053808-S3DS-200012483665_01_P001` | spa | 16 | radar |
| `20SEP09053_0030` | Test1 | `20SEP09053808-S3DS-200012483665_01_P001` | spa | 21 | radar |
| `20SEP09053_0032` | Test1 | `20SEP09053808-S3DS-200012483665_01_P001` | camo | 5 | radar |
| `21APR22040_0001` | Test1 | `21APR22040621-S3DS-200013119950_01_P001` | vehicle | 4 | radar |
| `21APR30054_0000` | Test1 | `21APR30054629-S3DS-200013142967_01_P001` | camo | 9 | radar |
| `21APR30054_0024` | Test1 | `21APR30054629-S3DS-200013142967_01_P001` | camo | 8 | radar |
| `21APR30054_0032` | Test1 | `21APR30054629-S3DS-200013142967_01_P001` | vehicle | 11 | radar |
| `21APR30054_0039` | Test1 | `21APR30054629-S3DS-200013142967_01_P001` | camo | 10 | radar |
| `21APR30054_0042` | Test1 | `21APR30054629-S3DS-200013142967_01_P001` | vehicle | 12 | radar |
| `21APR30054_0055` | Test1 | `21APR30054629-S3DS-200013142967_01_P001` | vehicle | 24 | radar |
| `21APR30054_0064` | Test1 | `21APR30054629-S3DS-200013142967_01_P001` | vehicle | 49 | radar |
| `21DEC12052_0089` | Test1 | `21DEC12052014-S3DS-200013142966_01_P001` | camo | 8 | radar |
| `21DEC27025_0005` | Test1 | `21DEC27025021-S3DS-200012895048_01_P001` | vehicle | 0 | radar |
| `21DEC27025_0008` | Test1 | `21DEC27025021-S3DS-200012895048_01_P001` | vehicle | 12 | radar |
| `21DEC27025_0009` | Test1 | `21DEC27025021-S3DS-200012895048_01_P001` | vehicle | 14 | radar |
| `21DEC27025_0026` | Test1 | `21DEC27025021-S3DS-200012895048_01_P001` | vehicle | 15 | radar |
| `21JAN25022_0005` | Test1 | `21JAN25022937-S3DS-200013104366_01_P001` | smallvehicle | 20 | radar |
| `21JAN25022_0019` | Test1 | `21JAN25022937-S3DS-200013104366_01_P001` | smallvehicle | 24 | radar |
| `21JAN25022_0025` | Test1 | `21JAN25022937-S3DS-200013104366_01_P001` | smallvehicle | 23 | radar |
| `21JAN25022_0028` | Test1 | `21JAN25022937-S3DS-200013104366_01_P001` | arty | 2 | radar |
| `21JAN25022_0029` | Test1 | `21JAN25022937-S3DS-200013104366_01_P001` | smallvehicle | 27 | radar |
| `21NOV24030_0067` | Test1 | `21NOV24030403-S3DS-200012895049_01_P001` | logistic | 98 | radar |
| `22DEC02022_0002` | Test1 | `22DEC02022210-S3DS-200013128267_01_P001` | arty | 3 | radar |
| `22FEB02032_0001` | Test1 | `22FEB02032525-S3DS-200012866245_01_P001` | camo | 19 | radar |
| `22FEB02032_0002` | Test1 | `22FEB02032525-S3DS-200012866245_01_P001` | camo | 8 | radar |
| `22FEB02032_0050` | Test1 | `22FEB02032525-S3DS-200012866245_01_P001` | camo | 5 | radar |
| `22OCT24030_0026` | Test1 | `22OCT24030421-S3DS-200011896352_01_P001` | radome | 57 | radar |
| `22OCT24030_0039` | Test1 | `22OCT24030421-S3DS-200011896352_01_P001` | logistic | 27 | radar |
| `22OCT24030_0065` | Test1 | `22OCT24030421-S3DS-200011896352_01_P001` | vehicle | 96 | radar |
| `22OCT24030_0073` | Test1 | `22OCT24030421-S3DS-200011896352_01_P001` | vehicle | 12 | radar |
| `22OCT24030_0089` | Test1 | `22OCT24030421-S3DS-200011896352_01_P001` | radome | 75 | radar |
| `23OCT24030_0019` | Test1 | `23OCT24030928-S3DS-200012400977_01_P001` | vehicle | 16 | radar |
| `24APR01051_0036` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | vehicle | 41 | radar |
| `24APR01051_0054` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | vehicle | 8 | radar |
| `24DEC21030_0004` | Test1 | `24DEC21030136-S3DS-200011913026_01_P001` | vehicle | 14 | radar |
| `24DEC21030_0011` | Test1 | `24DEC21030136-S3DS-200011913026_01_P001` | vehicle | 12 | radar |
| `24DEC21030_0012` | Test1 | `24DEC21030136-S3DS-200011913026_01_P001` | vehicle | 16 | radar |
| `24DEC21030_0014` | Test1 | `24DEC21030136-S3DS-200011913026_01_P001` | vehicle | 11 | radar |
| `24MAR27045_0000` | Test1 | `24MAR27045953-S3DS-200013168941_01_P001` | camo | 8 | radar |
| `24MAR27045_0001` | Test1 | `24MAR27045953-S3DS-200013168941_01_P001` | camo | 5 | radar |
| `24MAR27045_0003` | Test1 | `24MAR27045953-S3DS-200013168941_01_P001` | camo | 3 | radar |
| `24MAR27045_0012` | Test1 | `24MAR27045953-S3DS-200013168941_01_P001` | camo | 4 | radar |
| `25NOV29025_0002` | Test1 | `25NOV29025727-S3DS-200012895045_01_P001` | camo | 0 | radar |
| `25NOV29025_0017` | Test1 | `25NOV29025727-S3DS-200012895045_01_P001` | camo | 2 | radar |
| `26MAY09052_0006` | Test1 | `26MAY09052126-S3DS-200013142970_01_P001` | vehicle | 11 | radar |
| `26MAY09052_0035` | Test1 | `26MAY09052126-S3DS-200013142970_01_P001` | logistic | 32 | radar |
| `26MAY09052_0037` | Test1 | `26MAY09052126-S3DS-200013142970_01_P001` | vehicle | 22 | radar |
| `26MAY09052_0038` | Test1 | `26MAY09052126-S3DS-200013142970_01_P001` | smallvehicle | 34 | radar |
| `20SEP27061_0006` | Test2 | `20SEP27061806-S3DS-200011619312_01_P001` | vehicle | 13 | radar |
| `20SEP27061_0020` | Test2 | `20SEP27061806-S3DS-200011619312_01_P001` | vehicle | 5 | radar |
| `21APR18030_0015` | Test2 | `21APR18030819-S3DS-200013545084_01_P001` | vehicle | 29 | radar |
| `21APR18030_0060` | Test2 | `21APR18030819-S3DS-200013545084_01_P001` | tank | 35 | radar |
| `21APR18030_0068` | Test2 | `21APR18030819-S3DS-200013545084_01_P001` | smallvehicle | 30 | radar |
| `21APR18030_0071` | Test2 | `21APR18030819-S3DS-200013545084_01_P001` | vehicle | 33 | radar |
| `21APR18030_0074` | Test2 | `21APR18030819-S3DS-200013545084_01_P001` | tank | 34 | radar |
| `21APR18030_0097` | Test2 | `21APR18030819-S3DS-200013545084_01_P001` | vehicle | 45 | radar |
| `21APR18030_0105` | Test2 | `21APR18030819-S3DS-200013545084_01_P001` | tank | 39 | radar |
| `22APR14045_0012` | Test2 | `22APR14045506-S3DS-200013368123_01_P001` | vehicle | 16 | radar |
| `22OCT21045_0012` | Test2 | `22OCT21045409-S3DS-200012483671_01_P001` | camo | 59 | radar |
| `22OCT21045_0028` | Test2 | `22OCT21045409-S3DS-200012483671_01_P001` | tank | 158 | radar |
| `22OCT21045_0030` | Test2 | `22OCT21045409-S3DS-200012483671_01_P001` | camo | 58 | radar |
| `22OCT21045_0055` | Test2 | `22OCT21045409-S3DS-200012483671_01_P001` | camo | 55 | radar |
| `22OCT21045_0148` | Test2 | `22OCT21045409-S3DS-200012483671_01_P001` | camo | 60 | radar |
| `22OCT21045_0189` | Test2 | `22OCT21045409-S3DS-200012483671_01_P001` | camo | 27 | radar |
| `22OCT21045_0222` | Test2 | `22OCT21045409-S3DS-200012483671_01_P001` | camo | 10 | radar |
| `234045af_D_0004` | Test2 | `234045af_DS_PHR1B_201808290337504_FR1_PX_E108N34_0924_00286` | vehicle | 1 | radar |
| `23FEB01050_0046` | Test2 | `23FEB01050006-S3DS-200013142308_01_P001` | vehicle | 55 | radar |
| `23JAN10050_0003` | Test2 | `23JAN10050425-S3DS-200012483667_01_P001` | camo | 4 | radar |
| `23JAN10050_0004` | Test2 | `23JAN10050425-S3DS-200012483667_01_P001` | aerial | 13 | radar |
| `23JAN10050_0006` | Test2 | `23JAN10050425-S3DS-200012483667_01_P001` | camo | 3 | radar |
| `23JAN10050_0009` | Test2 | `23JAN10050425-S3DS-200012483667_01_P001` | camo | 2 | radar |
| `23JAN10050_0021` | Test2 | `23JAN10050425-S3DS-200012483667_01_P001` | camo | 18 | radar |
| `23MAY19062_0004` | Test2 | `23MAY19062258-S3DS-200011619589_01_P001` | vehicle | 43 | radar |
| `23MAY19062_0022` | Test2 | `23MAY19062258-S3DS-200011619589_01_P001` | logistic | 181 | radar |
| `23MAY19062_0034` | Test2 | `23MAY19062258-S3DS-200011619589_01_P001` | vehicle | 41 | radar |
| `23MAY19062_0041` | Test2 | `23MAY19062258-S3DS-200011619589_01_P001` | logistic | 180 | radar |
| `23MAY19062_0044` | Test2 | `23MAY19062258-S3DS-200011619589_01_P001` | vehicle | 48 | radar |
| `23MAY19062_0072` | Test2 | `23MAY19062258-S3DS-200011619589_01_P001` | vehicle | 37 | radar |
| `24DEC24042_0002` | Test2 | `24DEC24042920-S3DS-200013378864_01_P001` | camo | 2 | radar |
| `24DEC24042_0004` | Test2 | `24DEC24042920-S3DS-200013378864_01_P001` | vehicle | 13 | radar |
| `24DEC24042_0006` | Test2 | `24DEC24042920-S3DS-200013378864_01_P001` | vehicle | 14 | radar |
| `24DEC24042_0008` | Test2 | `24DEC24042920-S3DS-200013378864_01_P001` | camo | 0 | radar |
| `24DEC24042_0015` | Test2 | `24DEC24042920-S3DS-200013378864_01_P001` | vehicle | 11 | radar |
| `24NOV27054_0004` | Test2 | `24NOV27054611-S3DS-200012866946_01_P001` | vehicle | 11 | radar |
| `24OCT29045_0001` | Test2 | `24OCT29045607-S3DS-200013168961_01_P001` | vehicle | 13 | radar |
| `24OCT29045_0009` | Test2 | `24OCT29045607-S3DS-200013168961_01_P001` | vehicle | 12 | radar |
| `25DEC14052_0000` | Test2 | `25DEC14052859-S3DS-200011101282_01_P001` | radome | 3 | radar |
| `25DEC14052_0001` | Test2 | `25DEC14052859-S3DS-200011101282_01_P001` | radome | 4 | radar |
| `25JAN29042_0000` | Test2 | `25JAN29042609-S3DS-200013367959_01_P001` | radome | 6 | radar |
| `25JAN29042_0001` | Test2 | `25JAN29042609-S3DS-200013367959_01_P001` | radome | 5 | radar |
| `25JAN29042_0002` | Test2 | `25JAN29042609-S3DS-200013367959_01_P001` | camo | 0 | radar |
| `25JAN29042_0003` | Test2 | `25JAN29042609-S3DS-200013367959_01_P001` | camo | 1 | radar |
| `25MAR23054_0001` | Test2 | `25MAR23054346-S3DS-200011078330_01_P001` | vehicle | 0 | radar |
| `25MAR23054_0002` | Test2 | `25MAR23054346-S3DS-200011078330_01_P001` | vehicle | 16 | radar |
| `25MAR23054_0007` | Test2 | `25MAR23054346-S3DS-200011078330_01_P001` | vehicle | 3 | radar |
| `25MAR23054_0011` | Test2 | `25MAR23054346-S3DS-200011078330_01_P001` | vehicle | 18 | radar |
| `25MAR23054_0012` | Test2 | `25MAR23054346-S3DS-200011078330_01_P001` | smallvehicle | 12 | radar |
| `25MAR25043_0000` | Test2 | `25MAR25043103-S3DS-200011078671_01_P001` | radome | 4 | radar |
| `25MAR25043_0005` | Test2 | `25MAR25043103-S3DS-200011078671_01_P001` | vehicle | 5 | radar |
| `25NOV18044_0003` | Test2 | `25NOV18044741-S3DS-200011078376_01_P001` | vehicle | 12 | radar |
| `25NOV18044_0008` | Test2 | `25NOV18044741-S3DS-200011078376_01_P001` | radome | 7 | radar |
| `25NOV18044_0010` | Test2 | `25NOV18044741-S3DS-200011078376_01_P001` | logistic | 0 | radar |
| `26d44cd2_D_0042` | Test2 | `26d44cd2_DS_PHR1A_202012190354245_FR1_PX_E104N31_0306_00349` | vehicle | 61 | radar |
| `852dc76a_D_0004` | Test2 | `852dc76a_DS_PHR1B_202003280350581_FR1_PX_E102N27_0724_00333` | radome | 2 | radar |
| `852dc76a_D_0008` | Test2 | `852dc76a_DS_PHR1B_202003280350581_FR1_PX_E102N27_0724_00333` | smallvehicle | 42 | radar |
| `852dc76a_D_0010` | Test2 | `852dc76a_DS_PHR1B_202003280350581_FR1_PX_E102N27_0724_00333` | vehicle | 11 | radar |
| `852dc76a_D_0013` | Test2 | `852dc76a_DS_PHR1B_202003280350581_FR1_PX_E102N27_0724_00333` | smallvehicle | 17 | radar |
| `852dc76a_D_0016` | Test2 | `852dc76a_DS_PHR1B_202003280350581_FR1_PX_E102N27_0724_00333` | smallvehicle | 19 | radar |
| `852dc76a_D_0018` | Test2 | `852dc76a_DS_PHR1B_202003280350581_FR1_PX_E102N27_0724_00333` | vehicle | 12 | radar |
| `852dc76a_D_0024` | Test2 | `852dc76a_DS_PHR1B_202003280350581_FR1_PX_E102N27_0724_00333` | smallvehicle | 49 | radar |
| `d8bba13b_D_0014` | Test2 | `d8bba13b_DS_PHR1B_202109100317223_FR1_PX_E113N31_0818_00355` | vehicle | 28 | radar |

### background → radar: 95

| Instance ID | Split | Scene | Raw GT class | GT index (0-based) | Model answer |
|---|---|---|---|---:|---|
| `18JUN15032_0018` | Test1 | `18JUN15032547-S3DS-200012895053_01_P001` | background | unmatched | radar |
| `18MAR10025_0021` | Test1 | `18MAR10025634-S3DS-200012866237_01_P001` | background | unmatched | radar |
| `18MAR10025_0026` | Test1 | `18MAR10025634-S3DS-200012866237_01_P001` | background | unmatched | radar |
| `18MAY28024_0004` | Test1 | `18MAY28024731-S3DS-200013073805_01_P001` | background | unmatched | radar |
| `19DEC21034_0006` | Test1 | `19DEC21034631-S3DS-200013276864_01_P001` | background | unmatched | radar |
| `19MAY10032_0017` | Test1 | `19MAY10032935-S3DS-200012352046_01_P001` | background | unmatched | radar |
| `19MAY10032_0049` | Test1 | `19MAY10032935-S3DS-200012352046_01_P001` | background | unmatched | radar |
| `19SEP16023_0114` | Test1 | `19SEP16023725-S3DS-200011883557_01_P001` | background | unmatched | radar |
| `20MAR18030_0082` | Test1 | `20MAR18030857-S3DS-200012411145_01_P001` | background | unmatched | radar |
| `20NOV12043_0020` | Test1 | `20NOV12043850-S3DS-200012372799_01_P001` | background | unmatched | radar |
| `20SEP06040_0045` | Test1 | `20SEP06040719-S3DS-200013171123_01_P001` | background | unmatched | radar |
| `20SEP09053_0029` | Test1 | `20SEP09053808-S3DS-200012483665_01_P001` | background | unmatched | radar |
| `20SEP09053_0031` | Test1 | `20SEP09053808-S3DS-200012483665_01_P001` | background | unmatched | radar |
| `21APR14035_0001` | Test1 | `21APR14035937-S3DS-200013190861_01_P001` | background | unmatched | radar |
| `21APR14035_0003` | Test1 | `21APR14035937-S3DS-200013190861_01_P001` | background | unmatched | radar |
| `21APR30054_0037` | Test1 | `21APR30054629-S3DS-200013142967_01_P001` | background | unmatched | radar |
| `21APR30054_0052` | Test1 | `21APR30054629-S3DS-200013142967_01_P001` | background | unmatched | radar |
| `21APR30054_0058` | Test1 | `21APR30054629-S3DS-200013142967_01_P001` | background | unmatched | radar |
| `21APR30054_0066` | Test1 | `21APR30054629-S3DS-200013142967_01_P001` | background | unmatched | radar |
| `21DEC12052_0049` | Test1 | `21DEC12052014-S3DS-200013142966_01_P001` | background | unmatched | radar |
| `21DEC24025_0012` | Test1 | `21DEC24025812-S3DS-200013190737_01_P001` | background | unmatched | radar |
| `21JAN25022_0000` | Test1 | `21JAN25022937-S3DS-200013104366_01_P001` | background | unmatched | radar |
| `21JAN25022_0001` | Test1 | `21JAN25022937-S3DS-200013104366_01_P001` | background | unmatched | radar |
| `21JAN25022_0003` | Test1 | `21JAN25022937-S3DS-200013104366_01_P001` | background | unmatched | radar |
| `21JAN25022_0004` | Test1 | `21JAN25022937-S3DS-200013104366_01_P001` | background | unmatched | radar |
| `21JAN25022_0009` | Test1 | `21JAN25022937-S3DS-200013104366_01_P001` | background | unmatched | radar |
| `21JAN25022_0011` | Test1 | `21JAN25022937-S3DS-200013104366_01_P001` | background | unmatched | radar |
| `21JAN25022_0012` | Test1 | `21JAN25022937-S3DS-200013104366_01_P001` | background | unmatched | radar |
| `21JAN25022_0015` | Test1 | `21JAN25022937-S3DS-200013104366_01_P001` | background | unmatched | radar |
| `21JAN25022_0021` | Test1 | `21JAN25022937-S3DS-200013104366_01_P001` | background | unmatched | radar |
| `21JAN25022_0026` | Test1 | `21JAN25022937-S3DS-200013104366_01_P001` | background | unmatched | radar |
| `21JAN25022_0031` | Test1 | `21JAN25022937-S3DS-200013104366_01_P001` | background | unmatched | radar |
| `21JAN25022_0034` | Test1 | `21JAN25022937-S3DS-200013104366_01_P001` | background | unmatched | radar |
| `21JAN25022_0037` | Test1 | `21JAN25022937-S3DS-200013104366_01_P001` | background | unmatched | radar |
| `21NOV24030_0064` | Test1 | `21NOV24030403-S3DS-200012895049_01_P001` | background | unmatched | radar |
| `22DEC02022_0003` | Test1 | `22DEC02022210-S3DS-200013128267_01_P001` | background | unmatched | radar |
| `22DEC02022_0004` | Test1 | `22DEC02022210-S3DS-200013128267_01_P001` | background | unmatched | radar |
| `22FEB02032_0053` | Test1 | `22FEB02032525-S3DS-200012866245_01_P001` | background | unmatched | radar |
| `22OCT24030_0060` | Test1 | `22OCT24030421-S3DS-200011896352_01_P001` | background | unmatched | radar |
| `22OCT24030_0064` | Test1 | `22OCT24030421-S3DS-200011896352_01_P001` | background | unmatched | radar |
| `22OCT24030_0091` | Test1 | `22OCT24030421-S3DS-200011896352_01_P001` | background | unmatched | radar |
| `22OCT24030_0101` | Test1 | `22OCT24030421-S3DS-200011896352_01_P001` | background | unmatched | radar |
| `24APR01051_0066` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | background | unmatched | radar |
| `24APR01051_0068` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | background | unmatched | radar |
| `24MAR27045_0024` | Test1 | `24MAR27045953-S3DS-200013168941_01_P001` | background | unmatched | radar |
| `24MAR27045_0025` | Test1 | `24MAR27045953-S3DS-200013168941_01_P001` | background | unmatched | radar |
| `24MAR27045_0026` | Test1 | `24MAR27045953-S3DS-200013168941_01_P001` | background | unmatched | radar |
| `25NOV29025_0004` | Test1 | `25NOV29025727-S3DS-200012895045_01_P001` | background | unmatched | radar |
| `26APR20052_0004` | Test1 | `26APR20052910-S3DS-200013171094_01_P001` | background | unmatched | radar |
| `26MAY09052_0016` | Test1 | `26MAY09052126-S3DS-200013142970_01_P001` | background | unmatched | radar |
| `26MAY09052_0024` | Test1 | `26MAY09052126-S3DS-200013142970_01_P001` | background | unmatched | radar |
| `26MAY09052_0033` | Test1 | `26MAY09052126-S3DS-200013142970_01_P001` | background | unmatched | radar |
| `141d9464_D_0023` | Test2 | `141d9464_DS_PHR1B_202211150352306_FR1_PX_E103N26_0301_00320` | background | unmatched | radar |
| `19MAY14060_0006` | Test2 | `19MAY14060259-S3DS-200013142968_01_P001` | background | unmatched | radar |
| `19MAY14060_0008` | Test2 | `19MAY14060259-S3DS-200013142968_01_P001` | background | unmatched | radar |
| `19MAY14060_0011` | Test2 | `19MAY14060259-S3DS-200013142968_01_P001` | background | unmatched | radar |
| `20SEP27061_0016` | Test2 | `20SEP27061806-S3DS-200011619312_01_P001` | background | unmatched | radar |
| `20SEP27061_0018` | Test2 | `20SEP27061806-S3DS-200011619312_01_P001` | background | unmatched | radar |
| `21APR18030_0108` | Test2 | `21APR18030819-S3DS-200013545084_01_P001` | background | unmatched | radar |
| `21APR18030_0128` | Test2 | `21APR18030819-S3DS-200013545084_01_P001` | background | unmatched | radar |
| `22APR14045_0011` | Test2 | `22APR14045506-S3DS-200013368123_01_P001` | background | unmatched | radar |
| `22APR14045_0014` | Test2 | `22APR14045506-S3DS-200013368123_01_P001` | background | unmatched | radar |
| `22APR14045_0017` | Test2 | `22APR14045506-S3DS-200013368123_01_P001` | background | unmatched | radar |
| `22OCT21045_0219` | Test2 | `22OCT21045409-S3DS-200012483671_01_P001` | background | unmatched | radar |
| `22OCT21045_0271` | Test2 | `22OCT21045409-S3DS-200012483671_01_P001` | background | unmatched | radar |
| `23FEB01050_0019` | Test2 | `23FEB01050006-S3DS-200013142308_01_P001` | background | unmatched | radar |
| `23JAN10050_0002` | Test2 | `23JAN10050425-S3DS-200012483667_01_P001` | background | unmatched | radar |
| `23JAN10050_0019` | Test2 | `23JAN10050425-S3DS-200012483667_01_P001` | background | unmatched | radar |
| `23JAN10050_0020` | Test2 | `23JAN10050425-S3DS-200012483667_01_P001` | background | unmatched | radar |
| `23JAN10050_0022` | Test2 | `23JAN10050425-S3DS-200012483667_01_P001` | background | unmatched | radar |
| `23JAN15044_0584` | Test2 | `23JAN15044817-S3DS-200012483668_01_P001` | background | unmatched | radar |
| `23JAN30025_0256` | Test2 | `23JAN30025247-S3DS-200012319991_01_P001` | background | unmatched | radar |
| `23MAY19062_0070` | Test2 | `23MAY19062258-S3DS-200011619589_01_P001` | background | unmatched | radar |
| `24DEC24042_0005` | Test2 | `24DEC24042920-S3DS-200013378864_01_P001` | background | unmatched | radar |
| `24NOV27054_0003` | Test2 | `24NOV27054611-S3DS-200012866946_01_P001` | background | unmatched | radar |
| `24SEP08053_0010` | Test2 | `24SEP08053532-S3DS-200013142971_01_P001` | background | unmatched | radar |
| `25JAN29042_0004` | Test2 | `25JAN29042609-S3DS-200013367959_01_P001` | background | unmatched | radar |
| `25JAN29042_0010` | Test2 | `25JAN29042609-S3DS-200013367959_01_P001` | background | unmatched | radar |
| `25MAR23054_0000` | Test2 | `25MAR23054346-S3DS-200011078330_01_P001` | background | unmatched | radar |
| `25MAR23054_0014` | Test2 | `25MAR23054346-S3DS-200011078330_01_P001` | background | unmatched | radar |
| `25MAR23054_0015` | Test2 | `25MAR23054346-S3DS-200011078330_01_P001` | background | unmatched | radar |
| `25MAR23054_0016` | Test2 | `25MAR23054346-S3DS-200011078330_01_P001` | background | unmatched | radar |
| `25MAR23054_0017` | Test2 | `25MAR23054346-S3DS-200011078330_01_P001` | background | unmatched | radar |
| `25MAR23054_0018` | Test2 | `25MAR23054346-S3DS-200011078330_01_P001` | background | unmatched | radar |
| `25MAR23054_0020` | Test2 | `25MAR23054346-S3DS-200011078330_01_P001` | background | unmatched | radar |
| `25MAR23054_0024` | Test2 | `25MAR23054346-S3DS-200011078330_01_P001` | background | unmatched | radar |
| `25MAR25043_0001` | Test2 | `25MAR25043103-S3DS-200011078671_01_P001` | background | unmatched | radar |
| `25MAR25043_0007` | Test2 | `25MAR25043103-S3DS-200011078671_01_P001` | background | unmatched | radar |
| `25MAR25043_0009` | Test2 | `25MAR25043103-S3DS-200011078671_01_P001` | background | unmatched | radar |
| `25MAY16062_0042` | Test2 | `25MAY16062255-S3DS-200011655555_01_P001` | background | unmatched | radar |
| `25MAY16062_0070` | Test2 | `25MAY16062255-S3DS-200011655555_01_P001` | background | unmatched | radar |
| `25MAY16062_0079` | Test2 | `25MAY16062255-S3DS-200011655555_01_P001` | background | unmatched | radar |
| `25MAY16062_0081` | Test2 | `25MAY16062255-S3DS-200011655555_01_P001` | background | unmatched | radar |
| `25NOV18044_0005` | Test2 | `25NOV18044741-S3DS-200011078376_01_P001` | background | unmatched | radar |
| `d8bba13b_D_0029` | Test2 | `d8bba13b_DS_PHR1B_202109100317223_FR1_PX_E113N31_0818_00355` | background | unmatched | radar |

### radar → missile: 24

| Instance ID | Split | Scene | Raw GT class | GT index (0-based) | Model answer |
|---|---|---|---|---:|---|
| `19SEP16023_0021` | Test1 | `19SEP16023725-S3DS-200011883557_01_P001` | radar | 10 | missile |
| `21DEC12052_0088` | Test1 | `21DEC12052014-S3DS-200013142966_01_P001` | radar | 2 | missile |
| `21DEC27025_0012` | Test1 | `21DEC27025021-S3DS-200012895048_01_P001` | radar | 23 | missile |
| `21DEC27025_0024` | Test1 | `21DEC27025021-S3DS-200012895048_01_P001` | radar | 21 | missile |
| `21FEB15025_0000` | Test1 | `21FEB15025428-S3DS-200011883412_01_P001` | radar | 1 | missile |
| `21FEB15025_0002` | Test1 | `21FEB15025428-S3DS-200011883412_01_P001` | radar | 6 | missile |
| `21NOV24030_0044` | Test1 | `21NOV24030403-S3DS-200012895049_01_P001` | radar | 16 | missile |
| `22MAY03031_0010` | Test1 | `22MAY03031134-S3DS-200012804521_01_P001` | radar | 0 | missile |
| `22MAY03031_0021` | Test1 | `22MAY03031134-S3DS-200012804521_01_P001` | radar | 1 | missile |
| `22MAY03031_0022` | Test1 | `22MAY03031134-S3DS-200012804521_01_P001` | radar | 2 | missile |
| `22OCT24030_0024` | Test1 | `22OCT24030421-S3DS-200011896352_01_P001` | radar | 3 | missile |
| `22OCT24030_0027` | Test1 | `22OCT24030421-S3DS-200011896352_01_P001` | radar | 4 | missile |
| `22OCT24030_0081` | Test1 | `22OCT24030421-S3DS-200011896352_01_P001` | radar | 1 | missile |
| `23OCT24030_0018` | Test1 | `23OCT24030928-S3DS-200012400977_01_P001` | radar | 2 | missile |
| `23OCT24030_0023` | Test1 | `23OCT24030928-S3DS-200012400977_01_P001` | radar | 0 | missile |
| `23OCT24030_0025` | Test1 | `23OCT24030928-S3DS-200012400977_01_P001` | radar | 3 | missile |
| `24DEC21030_0008` | Test1 | `24DEC21030136-S3DS-200011913026_01_P001` | radar | 6 | missile |
| `24JAN04022_0057` | Test1 | `24JAN04022720-S3DS-200013055297_01_P001` | radar | 13 | missile |
| `24JAN04022_0082` | Test1 | `24JAN04022720-S3DS-200013055297_01_P001` | radar | 11 | missile |
| `141d9464_D_0003` | Test2 | `141d9464_DS_PHR1B_202211150352306_FR1_PX_E103N26_0301_00320` | radar | 1 | missile |
| `234045af_D_0019` | Test2 | `234045af_DS_PHR1B_201808290337504_FR1_PX_E108N34_0924_00286` | radar | 14 | missile |
| `234045af_D_0021` | Test2 | `234045af_DS_PHR1B_201808290337504_FR1_PX_E108N34_0924_00286` | radar | 13 | missile |
| `23JAN10050_0005` | Test2 | `23JAN10050425-S3DS-200012483667_01_P001` | radar | 15 | missile |
| `25JAN29042_0011` | Test2 | `25JAN29042609-S3DS-200013367959_01_P001` | radar | 8 | missile |

### radar → other: 17

| Instance ID | Split | Scene | Raw GT class | GT index (0-based) | Model answer |
|---|---|---|---|---:|---|
| `19SEP16023_0020` | Test1 | `19SEP16023725-S3DS-200011883557_01_P001` | radar | 6 | other |
| `21APR14035_0002` | Test1 | `21APR14035937-S3DS-200013190861_01_P001` | radar | 0 | other |
| `21NOV24030_0001` | Test1 | `21NOV24030403-S3DS-200012895049_01_P001` | radar | 18 | other |
| `21NOV24030_0010` | Test1 | `21NOV24030403-S3DS-200012895049_01_P001` | radar | 15 | other |
| `21NOV24030_0014` | Test1 | `21NOV24030403-S3DS-200012895049_01_P001` | radar | 17 | other |
| `21NOV24030_0018` | Test1 | `21NOV24030403-S3DS-200012895049_01_P001` | radar | 19 | other |
| `21NOV24030_0019` | Test1 | `21NOV24030403-S3DS-200012895049_01_P001` | radar | 21 | other |
| `21NOV24030_0022` | Test1 | `21NOV24030403-S3DS-200012895049_01_P001` | radar | 22 | other |
| `21NOV24030_0032` | Test1 | `21NOV24030403-S3DS-200012895049_01_P001` | radar | 20 | other |
| `22OCT24030_0003` | Test1 | `22OCT24030421-S3DS-200011896352_01_P001` | radar | 9 | other |
| `22OCT24030_0067` | Test1 | `22OCT24030421-S3DS-200011896352_01_P001` | radar | 10 | other |
| `22OCT24030_0100` | Test1 | `22OCT24030421-S3DS-200011896352_01_P001` | radar | 7 | other |
| `20SEP27061_0000` | Test2 | `20SEP27061806-S3DS-200011619312_01_P001` | radar | 7 | other |
| `20SEP27061_0014` | Test2 | `20SEP27061806-S3DS-200011619312_01_P001` | radar | 6 | other |
| `22MAR07045_0043` | Test2 | `22MAR07045331-S3DS-200013349499_01_P001` | radar | 111 | other |
| `22MAR07045_0119` | Test2 | `22MAR07045331-S3DS-200013349499_01_P001` | radar | 113 | other |
| `852dc76a_D_0015` | Test2 | `852dc76a_DS_PHR1B_202003280350581_FR1_PX_E102N27_0724_00333` | radar | 0 | other |

### radar → background: 0

No saved cases.


## Missile misclassification IDs

Completed C1 full clean Stage1 benchmark:confidence ≥0.50, polygon IoU ≥0.50. IDs identify detector proposals, not a newly assigned GT instance namespace. Full scene plus ID disambiguates source proposals. No new inference.

Other uses the historical non-target taxonomy, including radome; background means annotation-unmatched, not guaranteed empty. GT index is zero-based in the frozen parsed GT array. Model answer is class-only, with no rationale/confidence. Stage1 confidence belongs to the detector.

Unique errors in this ledger: **425**. Radar and missile ledgers overlap on the30 radar↔missile confusions; do not add them as independent errors.

### radar → missile: 24

| Instance ID | Split | Scene | Raw GT class | GT index (0-based) | Model answer |
|---|---|---|---|---:|---|
| `19SEP16023_0021` | Test1 | `19SEP16023725-S3DS-200011883557_01_P001` | radar | 10 | missile |
| `21DEC12052_0088` | Test1 | `21DEC12052014-S3DS-200013142966_01_P001` | radar | 2 | missile |
| `21DEC27025_0012` | Test1 | `21DEC27025021-S3DS-200012895048_01_P001` | radar | 23 | missile |
| `21DEC27025_0024` | Test1 | `21DEC27025021-S3DS-200012895048_01_P001` | radar | 21 | missile |
| `21FEB15025_0000` | Test1 | `21FEB15025428-S3DS-200011883412_01_P001` | radar | 1 | missile |
| `21FEB15025_0002` | Test1 | `21FEB15025428-S3DS-200011883412_01_P001` | radar | 6 | missile |
| `21NOV24030_0044` | Test1 | `21NOV24030403-S3DS-200012895049_01_P001` | radar | 16 | missile |
| `22MAY03031_0010` | Test1 | `22MAY03031134-S3DS-200012804521_01_P001` | radar | 0 | missile |
| `22MAY03031_0021` | Test1 | `22MAY03031134-S3DS-200012804521_01_P001` | radar | 1 | missile |
| `22MAY03031_0022` | Test1 | `22MAY03031134-S3DS-200012804521_01_P001` | radar | 2 | missile |
| `22OCT24030_0024` | Test1 | `22OCT24030421-S3DS-200011896352_01_P001` | radar | 3 | missile |
| `22OCT24030_0027` | Test1 | `22OCT24030421-S3DS-200011896352_01_P001` | radar | 4 | missile |
| `22OCT24030_0081` | Test1 | `22OCT24030421-S3DS-200011896352_01_P001` | radar | 1 | missile |
| `23OCT24030_0018` | Test1 | `23OCT24030928-S3DS-200012400977_01_P001` | radar | 2 | missile |
| `23OCT24030_0023` | Test1 | `23OCT24030928-S3DS-200012400977_01_P001` | radar | 0 | missile |
| `23OCT24030_0025` | Test1 | `23OCT24030928-S3DS-200012400977_01_P001` | radar | 3 | missile |
| `24DEC21030_0008` | Test1 | `24DEC21030136-S3DS-200011913026_01_P001` | radar | 6 | missile |
| `24JAN04022_0057` | Test1 | `24JAN04022720-S3DS-200013055297_01_P001` | radar | 13 | missile |
| `24JAN04022_0082` | Test1 | `24JAN04022720-S3DS-200013055297_01_P001` | radar | 11 | missile |
| `141d9464_D_0003` | Test2 | `141d9464_DS_PHR1B_202211150352306_FR1_PX_E103N26_0301_00320` | radar | 1 | missile |
| `234045af_D_0019` | Test2 | `234045af_DS_PHR1B_201808290337504_FR1_PX_E108N34_0924_00286` | radar | 14 | missile |
| `234045af_D_0021` | Test2 | `234045af_DS_PHR1B_201808290337504_FR1_PX_E108N34_0924_00286` | radar | 13 | missile |
| `23JAN10050_0005` | Test2 | `23JAN10050425-S3DS-200012483667_01_P001` | radar | 15 | missile |
| `25JAN29042_0011` | Test2 | `25JAN29042609-S3DS-200013367959_01_P001` | radar | 8 | missile |

### other → missile: 248

| Instance ID | Split | Scene | Raw GT class | GT index (0-based) | Model answer |
|---|---|---|---|---:|---|
| `18FEB10031_0005` | Test1 | `18FEB10031943-S3DS-200013190621_01_P001` | vehicle | 2 | missile |
| `18FEB10031_0006` | Test1 | `18FEB10031943-S3DS-200013190621_01_P001` | vehicle | 0 | missile |
| `18FEB10031_0008` | Test1 | `18FEB10031943-S3DS-200013190621_01_P001` | vehicle | 3 | missile |
| `18FEB10031_0017` | Test1 | `18FEB10031943-S3DS-200013190621_01_P001` | vehicle | 1 | missile |
| `18FEB10031_0036` | Test1 | `18FEB10031943-S3DS-200013190621_01_P001` | vehicle | 51 | missile |
| `18JUN15032_0006` | Test1 | `18JUN15032547-S3DS-200012895053_01_P001` | vehicle | 10 | missile |
| `18JUN15032_0008` | Test1 | `18JUN15032547-S3DS-200012895053_01_P001` | vehicle | 8 | missile |
| `18JUN15032_0013` | Test1 | `18JUN15032547-S3DS-200012895053_01_P001` | vehicle | 9 | missile |
| `18MAR10025_0003` | Test1 | `18MAR10025634-S3DS-200012866237_01_P001` | vehicle | 1 | missile |
| `18MAR10025_0008` | Test1 | `18MAR10025634-S3DS-200012866237_01_P001` | vehicle | 0 | missile |
| `19DEC21034_0004` | Test1 | `19DEC21034631-S3DS-200013276864_01_P001` | vehicle | 4 | missile |
| `19MAR13040_0006` | Test1 | `19MAR13040701-S3DS-200013268578_01_P001` | vehicle | 10 | missile |
| `19MAY10032_0032` | Test1 | `19MAY10032935-S3DS-200012352046_01_P001` | vehicle | 2 | missile |
| `19MAY10032_0034` | Test1 | `19MAY10032935-S3DS-200012352046_01_P001` | vehicle | 53 | missile |
| `19SEP16023_0000` | Test1 | `19SEP16023725-S3DS-200011883557_01_P001` | vehicle | 60 | missile |
| `19SEP16023_0010` | Test1 | `19SEP16023725-S3DS-200011883557_01_P001` | logistic | 78 | missile |
| `19SEP16023_0011` | Test1 | `19SEP16023725-S3DS-200011883557_01_P001` | logistic | 79 | missile |
| `19SEP16023_0013` | Test1 | `19SEP16023725-S3DS-200011883557_01_P001` | smallvehicle | 48 | missile |
| `19SEP16023_0024` | Test1 | `19SEP16023725-S3DS-200011883557_01_P001` | vehicle | 2 | missile |
| `19SEP16023_0033` | Test1 | `19SEP16023725-S3DS-200011883557_01_P001` | vehicle | 37 | missile |
| `19SEP16023_0037` | Test1 | `19SEP16023725-S3DS-200011883557_01_P001` | vehicle | 13 | missile |
| `19SEP16023_0049` | Test1 | `19SEP16023725-S3DS-200011883557_01_P001` | vehicle | 20 | missile |
| `19SEP16023_0057` | Test1 | `19SEP16023725-S3DS-200011883557_01_P001` | vehicle | 38 | missile |
| `19SEP16023_0058` | Test1 | `19SEP16023725-S3DS-200011883557_01_P001` | vehicle | 99 | missile |
| `19SEP16023_0080` | Test1 | `19SEP16023725-S3DS-200011883557_01_P001` | vehicle | 3 | missile |
| `19SEP16023_0087` | Test1 | `19SEP16023725-S3DS-200011883557_01_P001` | vehicle | 12 | missile |
| `19SEP16023_0096` | Test1 | `19SEP16023725-S3DS-200011883557_01_P001` | vehicle | 73 | missile |
| `19SEP16023_0106` | Test1 | `19SEP16023725-S3DS-200011883557_01_P001` | vehicle | 39 | missile |
| `19SEP16023_0124` | Test1 | `19SEP16023725-S3DS-200011883557_01_P001` | vehicle | 4 | missile |
| `19SEP16023_0130` | Test1 | `19SEP16023725-S3DS-200011883557_01_P001` | vehicle | 33 | missile |
| `20NOV12043_0000` | Test1 | `20NOV12043850-S3DS-200012372799_01_P001` | vehicle | 24 | missile |
| `20NOV12043_0001` | Test1 | `20NOV12043850-S3DS-200012372799_01_P001` | vehicle | 8 | missile |
| `20SEP06040_0003` | Test1 | `20SEP06040719-S3DS-200013171123_01_P001` | vehicle | 11 | missile |
| `20SEP06040_0004` | Test1 | `20SEP06040719-S3DS-200013171123_01_P001` | vehicle | 7 | missile |
| `20SEP06040_0005` | Test1 | `20SEP06040719-S3DS-200013171123_01_P001` | vehicle | 8 | missile |
| `20SEP06040_0009` | Test1 | `20SEP06040719-S3DS-200013171123_01_P001` | vehicle | 4 | missile |
| `20SEP06040_0013` | Test1 | `20SEP06040719-S3DS-200013171123_01_P001` | vehicle | 13 | missile |
| `20SEP06040_0014` | Test1 | `20SEP06040719-S3DS-200013171123_01_P001` | vehicle | 24 | missile |
| `20SEP06040_0015` | Test1 | `20SEP06040719-S3DS-200013171123_01_P001` | vehicle | 28 | missile |
| `20SEP06040_0016` | Test1 | `20SEP06040719-S3DS-200013171123_01_P001` | vehicle | 26 | missile |
| `20SEP06040_0017` | Test1 | `20SEP06040719-S3DS-200013171123_01_P001` | vehicle | 14 | missile |
| `20SEP06040_0020` | Test1 | `20SEP06040719-S3DS-200013171123_01_P001` | vehicle | 12 | missile |
| `20SEP06040_0021` | Test1 | `20SEP06040719-S3DS-200013171123_01_P001` | vehicle | 25 | missile |
| `20SEP06040_0030` | Test1 | `20SEP06040719-S3DS-200013171123_01_P001` | vehicle | 27 | missile |
| `20SEP06040_0041` | Test1 | `20SEP06040719-S3DS-200013171123_01_P001` | vehicle | 15 | missile |
| `20SEP09053_0014` | Test1 | `20SEP09053808-S3DS-200012483665_01_P001` | vehicle | 34 | missile |
| `20SEP09053_0022` | Test1 | `20SEP09053808-S3DS-200012483665_01_P001` | logistic | 60 | missile |
| `21APR30054_0005` | Test1 | `21APR30054629-S3DS-200013142967_01_P001` | vehicle | 25 | missile |
| `21APR30054_0012` | Test1 | `21APR30054629-S3DS-200013142967_01_P001` | vehicle | 20 | missile |
| `21APR30054_0047` | Test1 | `21APR30054629-S3DS-200013142967_01_P001` | vehicle | 71 | missile |
| `21APR30054_0053` | Test1 | `21APR30054629-S3DS-200013142967_01_P001` | vehicle | 72 | missile |
| `21DEC12052_0002` | Test1 | `21DEC12052014-S3DS-200013142966_01_P001` | vehicle | 28 | missile |
| `21DEC12052_0003` | Test1 | `21DEC12052014-S3DS-200013142966_01_P001` | vehicle | 31 | missile |
| `21DEC12052_0005` | Test1 | `21DEC12052014-S3DS-200013142966_01_P001` | vehicle | 30 | missile |
| `21DEC12052_0007` | Test1 | `21DEC12052014-S3DS-200013142966_01_P001` | vehicle | 36 | missile |
| `21DEC12052_0010` | Test1 | `21DEC12052014-S3DS-200013142966_01_P001` | vehicle | 34 | missile |
| `21DEC12052_0011` | Test1 | `21DEC12052014-S3DS-200013142966_01_P001` | vehicle | 35 | missile |
| `21DEC12052_0012` | Test1 | `21DEC12052014-S3DS-200013142966_01_P001` | vehicle | 39 | missile |
| `21DEC12052_0016` | Test1 | `21DEC12052014-S3DS-200013142966_01_P001` | vehicle | 37 | missile |
| `21DEC12052_0017` | Test1 | `21DEC12052014-S3DS-200013142966_01_P001` | vehicle | 41 | missile |
| `21DEC12052_0021` | Test1 | `21DEC12052014-S3DS-200013142966_01_P001` | vehicle | 48 | missile |
| `21DEC12052_0022` | Test1 | `21DEC12052014-S3DS-200013142966_01_P001` | vehicle | 13 | missile |
| `21DEC12052_0024` | Test1 | `21DEC12052014-S3DS-200013142966_01_P001` | vehicle | 44 | missile |
| `21DEC12052_0028` | Test1 | `21DEC12052014-S3DS-200013142966_01_P001` | vehicle | 21 | missile |
| `21DEC12052_0029` | Test1 | `21DEC12052014-S3DS-200013142966_01_P001` | vehicle | 38 | missile |
| `21DEC12052_0034` | Test1 | `21DEC12052014-S3DS-200013142966_01_P001` | vehicle | 33 | missile |
| `21DEC12052_0035` | Test1 | `21DEC12052014-S3DS-200013142966_01_P001` | vehicle | 43 | missile |
| `21DEC12052_0042` | Test1 | `21DEC12052014-S3DS-200013142966_01_P001` | vehicle | 12 | missile |
| `21DEC12052_0068` | Test1 | `21DEC12052014-S3DS-200013142966_01_P001` | smallvehicle | 83 | missile |
| `21DEC24025_0000` | Test1 | `21DEC24025812-S3DS-200013190737_01_P001` | vehicle | 4 | missile |
| `21DEC24025_0001` | Test1 | `21DEC24025812-S3DS-200013190737_01_P001` | vehicle | 14 | missile |
| `21DEC24025_0002` | Test1 | `21DEC24025812-S3DS-200013190737_01_P001` | vehicle | 7 | missile |
| `21DEC24025_0004` | Test1 | `21DEC24025812-S3DS-200013190737_01_P001` | vehicle | 12 | missile |
| `21DEC24025_0007` | Test1 | `21DEC24025812-S3DS-200013190737_01_P001` | vehicle | 3 | missile |
| `21DEC27025_0011` | Test1 | `21DEC27025021-S3DS-200012895048_01_P001` | vehicle | 7 | missile |
| `21DEC27025_0013` | Test1 | `21DEC27025021-S3DS-200012895048_01_P001` | vehicle | 13 | missile |
| `21DEC27025_0015` | Test1 | `21DEC27025021-S3DS-200012895048_01_P001` | vehicle | 10 | missile |
| `21DEC27025_0021` | Test1 | `21DEC27025021-S3DS-200012895048_01_P001` | vehicle | 18 | missile |
| `21DEC27025_0023` | Test1 | `21DEC27025021-S3DS-200012895048_01_P001` | smallvehicle | 24 | missile |
| `21DEC27025_0025` | Test1 | `21DEC27025021-S3DS-200012895048_01_P001` | vehicle | 19 | missile |
| `21NOV24030_0003` | Test1 | `21NOV24030403-S3DS-200012895049_01_P001` | vehicle | 30 | missile |
| `21NOV24030_0008` | Test1 | `21NOV24030403-S3DS-200012895049_01_P001` | vehicle | 31 | missile |
| `21NOV24030_0016` | Test1 | `21NOV24030403-S3DS-200012895049_01_P001` | vehicle | 33 | missile |
| `21NOV24030_0028` | Test1 | `21NOV24030403-S3DS-200012895049_01_P001` | vehicle | 34 | missile |
| `21NOV24030_0055` | Test1 | `21NOV24030403-S3DS-200012895049_01_P001` | vehicle | 24 | missile |
| `21NOV24030_0063` | Test1 | `21NOV24030403-S3DS-200012895049_01_P001` | vehicle | 25 | missile |
| `21NOV24030_0076` | Test1 | `21NOV24030403-S3DS-200012895049_01_P001` | logistic | 39 | missile |
| `21NOV24030_0079` | Test1 | `21NOV24030403-S3DS-200012895049_01_P001` | camo | 0 | missile |
| `21NOV24030_0081` | Test1 | `21NOV24030403-S3DS-200012895049_01_P001` | camo | 1 | missile |
| `21NOV24030_0083` | Test1 | `21NOV24030403-S3DS-200012895049_01_P001` | camo | 9 | missile |
| `22FEB02032_0005` | Test1 | `22FEB02032525-S3DS-200012866245_01_P001` | vehicle | 21 | missile |
| `22MAY03031_0003` | Test1 | `22MAY03031134-S3DS-200012804521_01_P001` | vehicle | 8 | missile |
| `22MAY03031_0011` | Test1 | `22MAY03031134-S3DS-200012804521_01_P001` | vehicle | 31 | missile |
| `22MAY03031_0015` | Test1 | `22MAY03031134-S3DS-200012804521_01_P001` | vehicle | 35 | missile |
| `22MAY03031_0018` | Test1 | `22MAY03031134-S3DS-200012804521_01_P001` | vehicle | 33 | missile |
| `22MAY03031_0020` | Test1 | `22MAY03031134-S3DS-200012804521_01_P001` | vehicle | 28 | missile |
| `22MAY03031_0041` | Test1 | `22MAY03031134-S3DS-200012804521_01_P001` | vehicle | 22 | missile |
| `22MAY03031_0042` | Test1 | `22MAY03031134-S3DS-200012804521_01_P001` | vehicle | 34 | missile |
| `22OCT24030_0001` | Test1 | `22OCT24030421-S3DS-200011896352_01_P001` | vehicle | 24 | missile |
| `22OCT24030_0002` | Test1 | `22OCT24030421-S3DS-200011896352_01_P001` | vehicle | 84 | missile |
| `22OCT24030_0004` | Test1 | `22OCT24030421-S3DS-200011896352_01_P001` | vehicle | 22 | missile |
| `22OCT24030_0007` | Test1 | `22OCT24030421-S3DS-200011896352_01_P001` | vehicle | 21 | missile |
| `22OCT24030_0017` | Test1 | `22OCT24030421-S3DS-200011896352_01_P001` | vehicle | 85 | missile |
| `22OCT24030_0033` | Test1 | `22OCT24030421-S3DS-200011896352_01_P001` | logistic | 0 | missile |
| `22OCT24030_0038` | Test1 | `22OCT24030421-S3DS-200011896352_01_P001` | vehicle | 20 | missile |
| `23OCT24030_0001` | Test1 | `23OCT24030928-S3DS-200012400977_01_P001` | vehicle | 12 | missile |
| `23OCT24030_0003` | Test1 | `23OCT24030928-S3DS-200012400977_01_P001` | vehicle | 18 | missile |
| `23OCT24030_0005` | Test1 | `23OCT24030928-S3DS-200012400977_01_P001` | vehicle | 17 | missile |
| `23OCT24030_0008` | Test1 | `23OCT24030928-S3DS-200012400977_01_P001` | vehicle | 15 | missile |
| `23OCT24030_0012` | Test1 | `23OCT24030928-S3DS-200012400977_01_P001` | vehicle | 19 | missile |
| `23OCT24030_0014` | Test1 | `23OCT24030928-S3DS-200012400977_01_P001` | vehicle | 20 | missile |
| `23OCT24030_0015` | Test1 | `23OCT24030928-S3DS-200012400977_01_P001` | vehicle | 9 | missile |
| `24APR01051_0037` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | vehicle | 45 | missile |
| `24DEC21030_0001` | Test1 | `24DEC21030136-S3DS-200011913026_01_P001` | vehicle | 7 | missile |
| `24DEC21030_0002` | Test1 | `24DEC21030136-S3DS-200011913026_01_P001` | vehicle | 20 | missile |
| `24DEC21030_0013` | Test1 | `24DEC21030136-S3DS-200011913026_01_P001` | smallvehicle | 15 | missile |
| `24DEC21030_0015` | Test1 | `24DEC21030136-S3DS-200011913026_01_P001` | logistic | 13 | missile |
| `24DEC21030_0016` | Test1 | `24DEC21030136-S3DS-200011913026_01_P001` | smallvehicle | 17 | missile |
| `24DEC21030_0018` | Test1 | `24DEC21030136-S3DS-200011913026_01_P001` | smallvehicle | 18 | missile |
| `24JAN04022_0001` | Test1 | `24JAN04022720-S3DS-200013055297_01_P001` | vehicle | 22 | missile |
| `24JAN04022_0005` | Test1 | `24JAN04022720-S3DS-200013055297_01_P001` | vehicle | 21 | missile |
| `24JAN04022_0008` | Test1 | `24JAN04022720-S3DS-200013055297_01_P001` | vehicle | 23 | missile |
| `24JAN04022_0018` | Test1 | `24JAN04022720-S3DS-200013055297_01_P001` | vehicle | 24 | missile |
| `24JAN04022_0060` | Test1 | `24JAN04022720-S3DS-200013055297_01_P001` | logistic | 36 | missile |
| `24JAN04022_0069` | Test1 | `24JAN04022720-S3DS-200013055297_01_P001` | logistic | 35 | missile |
| `24MAR27045_0018` | Test1 | `24MAR27045953-S3DS-200013168941_01_P001` | vehicle | 15 | missile |
| `24MAR27045_0022` | Test1 | `24MAR27045953-S3DS-200013168941_01_P001` | camo | 7 | missile |
| `26APR20052_0000` | Test1 | `26APR20052910-S3DS-200013171094_01_P001` | vehicle | 16 | missile |
| `19MAY14060_0002` | Test2 | `19MAY14060259-S3DS-200013142968_01_P001` | vehicle | 4 | missile |
| `19MAY14060_0003` | Test2 | `19MAY14060259-S3DS-200013142968_01_P001` | vehicle | 5 | missile |
| `21APR18030_0025` | Test2 | `21APR18030819-S3DS-200013545084_01_P001` | vehicle | 18 | missile |
| `21APR18030_0039` | Test2 | `21APR18030819-S3DS-200013545084_01_P001` | spa | 12 | missile |
| `21APR18030_0043` | Test2 | `21APR18030819-S3DS-200013545084_01_P001` | vehicle | 17 | missile |
| `21APR18030_0058` | Test2 | `21APR18030819-S3DS-200013545084_01_P001` | spa | 11 | missile |
| `21APR18030_0059` | Test2 | `21APR18030819-S3DS-200013545084_01_P001` | tank | 50 | missile |
| `21APR18030_0064` | Test2 | `21APR18030819-S3DS-200013545084_01_P001` | tank | 13 | missile |
| `21APR18030_0067` | Test2 | `21APR18030819-S3DS-200013545084_01_P001` | tank | 8 | missile |
| `21APR18030_0080` | Test2 | `21APR18030819-S3DS-200013545084_01_P001` | spa | 70 | missile |
| `21APR18030_0085` | Test2 | `21APR18030819-S3DS-200013545084_01_P001` | tank | 48 | missile |
| `21APR18030_0089` | Test2 | `21APR18030819-S3DS-200013545084_01_P001` | tank | 16 | missile |
| `21APR18030_0098` | Test2 | `21APR18030819-S3DS-200013545084_01_P001` | tank | 7 | missile |
| `21APR18030_0109` | Test2 | `21APR18030819-S3DS-200013545084_01_P001` | tank | 75 | missile |
| `22APR14045_0001` | Test2 | `22APR14045506-S3DS-200013368123_01_P001` | vehicle | 1 | missile |
| `22APR14045_0006` | Test2 | `22APR14045506-S3DS-200013368123_01_P001` | vehicle | 2 | missile |
| `22APR14045_0013` | Test2 | `22APR14045506-S3DS-200013368123_01_P001` | vehicle | 0 | missile |
| `22APR14045_0023` | Test2 | `22APR14045506-S3DS-200013368123_01_P001` | camo | 4 | missile |
| `22MAR02025_0005` | Test2 | `22MAR02025946-S3DS-200012804518_01_P001` | vehicle | 17 | missile |
| `22MAR02025_0009` | Test2 | `22MAR02025946-S3DS-200012804518_01_P001` | vehicle | 38 | missile |
| `22MAR02025_0021` | Test2 | `22MAR02025946-S3DS-200012804518_01_P001` | vehicle | 97 | missile |
| `22MAR02025_0050` | Test2 | `22MAR02025946-S3DS-200012804518_01_P001` | vehicle | 92 | missile |
| `22MAR02025_0072` | Test2 | `22MAR02025946-S3DS-200012804518_01_P001` | vehicle | 28 | missile |
| `22MAR02025_0095` | Test2 | `22MAR02025946-S3DS-200012804518_01_P001` | smallvehicle | 31 | missile |
| `22OCT21045_0046` | Test2 | `22OCT21045409-S3DS-200012483671_01_P001` | tank | 115 | missile |
| `22OCT21045_0084` | Test2 | `22OCT21045409-S3DS-200012483671_01_P001` | tank | 99 | missile |
| `22OCT21045_0090` | Test2 | `22OCT21045409-S3DS-200012483671_01_P001` | tank | 98 | missile |
| `22OCT21045_0092` | Test2 | `22OCT21045409-S3DS-200012483671_01_P001` | tank | 112 | missile |
| `22OCT21045_0156` | Test2 | `22OCT21045409-S3DS-200012483671_01_P001` | tank | 119 | missile |
| `22OCT21045_0159` | Test2 | `22OCT21045409-S3DS-200012483671_01_P001` | camo | 57 | missile |
| `22OCT21045_0163` | Test2 | `22OCT21045409-S3DS-200012483671_01_P001` | tank | 109 | missile |
| `22OCT21045_0191` | Test2 | `22OCT21045409-S3DS-200012483671_01_P001` | camo | 56 | missile |
| `22OCT21045_0226` | Test2 | `22OCT21045409-S3DS-200012483671_01_P001` | tank | 120 | missile |
| `234045af_D_0003` | Test2 | `234045af_DS_PHR1B_201808290337504_FR1_PX_E108N34_0924_00286` | vehicle | 7 | missile |
| `234045af_D_0006` | Test2 | `234045af_DS_PHR1B_201808290337504_FR1_PX_E108N34_0924_00286` | vehicle | 10 | missile |
| `234045af_D_0007` | Test2 | `234045af_DS_PHR1B_201808290337504_FR1_PX_E108N34_0924_00286` | vehicle | 15 | missile |
| `234045af_D_0010` | Test2 | `234045af_DS_PHR1B_201808290337504_FR1_PX_E108N34_0924_00286` | vehicle | 0 | missile |
| `234045af_D_0011` | Test2 | `234045af_DS_PHR1B_201808290337504_FR1_PX_E108N34_0924_00286` | vehicle | 18 | missile |
| `234045af_D_0013` | Test2 | `234045af_DS_PHR1B_201808290337504_FR1_PX_E108N34_0924_00286` | vehicle | 17 | missile |
| `234045af_D_0015` | Test2 | `234045af_DS_PHR1B_201808290337504_FR1_PX_E108N34_0924_00286` | vehicle | 27 | missile |
| `234045af_D_0016` | Test2 | `234045af_DS_PHR1B_201808290337504_FR1_PX_E108N34_0924_00286` | vehicle | 4 | missile |
| `234045af_D_0020` | Test2 | `234045af_DS_PHR1B_201808290337504_FR1_PX_E108N34_0924_00286` | vehicle | 16 | missile |
| `234045af_D_0030` | Test2 | `234045af_DS_PHR1B_201808290337504_FR1_PX_E108N34_0924_00286` | vehicle | 20 | missile |
| `23FEB01050_0010` | Test2 | `23FEB01050006-S3DS-200013142308_01_P001` | vehicle | 53 | missile |
| `23FEB01050_0014` | Test2 | `23FEB01050006-S3DS-200013142308_01_P001` | vehicle | 54 | missile |
| `23FEB01050_0015` | Test2 | `23FEB01050006-S3DS-200013142308_01_P001` | vehicle | 52 | missile |
| `23FEB01050_0021` | Test2 | `23FEB01050006-S3DS-200013142308_01_P001` | vehicle | 51 | missile |
| `23JAN10050_0008` | Test2 | `23JAN10050425-S3DS-200012483667_01_P001` | vehicle | 16 | missile |
| `23MAY19062_0002` | Test2 | `23MAY19062258-S3DS-200011619589_01_P001` | vehicle | 55 | missile |
| `23MAY19062_0006` | Test2 | `23MAY19062258-S3DS-200011619589_01_P001` | vehicle | 20 | missile |
| `23MAY19062_0042` | Test2 | `23MAY19062258-S3DS-200011619589_01_P001` | logistic | 182 | missile |
| `24APR06053_0007` | Test2 | `24APR06053032-S3DS-200013392575_01_P001` | camo | 86 | missile |
| `24APR06053_0010` | Test2 | `24APR06053032-S3DS-200013392575_01_P001` | camo | 18 | missile |
| `24APR06053_0014` | Test2 | `24APR06053032-S3DS-200013392575_01_P001` | camo | 84 | missile |
| `24DEC24042_0000` | Test2 | `24DEC24042920-S3DS-200013378864_01_P001` | vehicle | 5 | missile |
| `24DEC24042_0001` | Test2 | `24DEC24042920-S3DS-200013378864_01_P001` | vehicle | 4 | missile |
| `24DEC24042_0003` | Test2 | `24DEC24042920-S3DS-200013378864_01_P001` | vehicle | 6 | missile |
| `24DEC24042_0012` | Test2 | `24DEC24042920-S3DS-200013378864_01_P001` | vehicle | 9 | missile |
| `24DEC24042_0014` | Test2 | `24DEC24042920-S3DS-200013378864_01_P001` | vehicle | 12 | missile |
| `24NOV27054_0000` | Test2 | `24NOV27054611-S3DS-200012866946_01_P001` | vehicle | 6 | missile |
| `24NOV27054_0001` | Test2 | `24NOV27054611-S3DS-200012866946_01_P001` | vehicle | 8 | missile |
| `24NOV27054_0002` | Test2 | `24NOV27054611-S3DS-200012866946_01_P001` | vehicle | 7 | missile |
| `24NOV27054_0005` | Test2 | `24NOV27054611-S3DS-200012866946_01_P001` | vehicle | 9 | missile |
| `24NOV27054_0007` | Test2 | `24NOV27054611-S3DS-200012866946_01_P001` | vehicle | 18 | missile |
| `24NOV27054_0008` | Test2 | `24NOV27054611-S3DS-200012866946_01_P001` | vehicle | 10 | missile |
| `24OCT29045_0000` | Test2 | `24OCT29045607-S3DS-200013168961_01_P001` | aerial | 7 | missile |
| `24OCT29045_0003` | Test2 | `24OCT29045607-S3DS-200013168961_01_P001` | vehicle | 14 | missile |
| `24SEP08053_0000` | Test2 | `24SEP08053532-S3DS-200013142971_01_P001` | vehicle | 7 | missile |
| `24SEP08053_0004` | Test2 | `24SEP08053532-S3DS-200013142971_01_P001` | vehicle | 1 | missile |
| `25JAN29042_0005` | Test2 | `25JAN29042609-S3DS-200013367959_01_P001` | vehicle | 7 | missile |
| `25JAN29042_0008` | Test2 | `25JAN29042609-S3DS-200013367959_01_P001` | camo | 2 | missile |
| `25MAR23054_0013` | Test2 | `25MAR23054346-S3DS-200011078330_01_P001` | smallvehicle | 11 | missile |
| `25MAR31055_0002` | Test2 | `25MAR31055119-S3DS-200012804523_01_P001` | vehicle | 4 | missile |
| `25MAR31055_0003` | Test2 | `25MAR31055119-S3DS-200012804523_01_P001` | smallvehicle | 10 | missile |
| `25MAY16062_0034` | Test2 | `25MAY16062255-S3DS-200011655555_01_P001` | vehicle | 22 | missile |
| `25MAY16062_0065` | Test2 | `25MAY16062255-S3DS-200011655555_01_P001` | vehicle | 13 | missile |
| `25MAY16062_0075` | Test2 | `25MAY16062255-S3DS-200011655555_01_P001` | vehicle | 61 | missile |
| `26d44cd2_D_0015` | Test2 | `26d44cd2_DS_PHR1A_202012190354245_FR1_PX_E104N31_0306_00349` | vehicle | 21 | missile |
| `26d44cd2_D_0020` | Test2 | `26d44cd2_DS_PHR1A_202012190354245_FR1_PX_E104N31_0306_00349` | vehicle | 25 | missile |
| `26d44cd2_D_0024` | Test2 | `26d44cd2_DS_PHR1A_202012190354245_FR1_PX_E104N31_0306_00349` | vehicle | 20 | missile |
| `26d44cd2_D_0026` | Test2 | `26d44cd2_DS_PHR1A_202012190354245_FR1_PX_E104N31_0306_00349` | vehicle | 16 | missile |
| `26d44cd2_D_0028` | Test2 | `26d44cd2_DS_PHR1A_202012190354245_FR1_PX_E104N31_0306_00349` | vehicle | 31 | missile |
| `26d44cd2_D_0031` | Test2 | `26d44cd2_DS_PHR1A_202012190354245_FR1_PX_E104N31_0306_00349` | vehicle | 19 | missile |
| `26d44cd2_D_0034` | Test2 | `26d44cd2_DS_PHR1A_202012190354245_FR1_PX_E104N31_0306_00349` | vehicle | 22 | missile |
| `26d44cd2_D_0036` | Test2 | `26d44cd2_DS_PHR1A_202012190354245_FR1_PX_E104N31_0306_00349` | vehicle | 18 | missile |
| `26d44cd2_D_0044` | Test2 | `26d44cd2_DS_PHR1A_202012190354245_FR1_PX_E104N31_0306_00349` | vehicle | 26 | missile |
| `26d44cd2_D_0045` | Test2 | `26d44cd2_DS_PHR1A_202012190354245_FR1_PX_E104N31_0306_00349` | vehicle | 29 | missile |
| `26d44cd2_D_0049` | Test2 | `26d44cd2_DS_PHR1A_202012190354245_FR1_PX_E104N31_0306_00349` | vehicle | 60 | missile |
| `26d44cd2_D_0050` | Test2 | `26d44cd2_DS_PHR1A_202012190354245_FR1_PX_E104N31_0306_00349` | vehicle | 32 | missile |
| `26d44cd2_D_0052` | Test2 | `26d44cd2_DS_PHR1A_202012190354245_FR1_PX_E104N31_0306_00349` | vehicle | 34 | missile |
| `26d44cd2_D_0053` | Test2 | `26d44cd2_DS_PHR1A_202012190354245_FR1_PX_E104N31_0306_00349` | vehicle | 59 | missile |
| `852dc76a_D_0000` | Test2 | `852dc76a_DS_PHR1B_202003280350581_FR1_PX_E102N27_0724_00333` | vehicle | 14 | missile |
| `852dc76a_D_0001` | Test2 | `852dc76a_DS_PHR1B_202003280350581_FR1_PX_E102N27_0724_00333` | vehicle | 26 | missile |
| `852dc76a_D_0002` | Test2 | `852dc76a_DS_PHR1B_202003280350581_FR1_PX_E102N27_0724_00333` | vehicle | 32 | missile |
| `852dc76a_D_0003` | Test2 | `852dc76a_DS_PHR1B_202003280350581_FR1_PX_E102N27_0724_00333` | vehicle | 28 | missile |
| `852dc76a_D_0005` | Test2 | `852dc76a_DS_PHR1B_202003280350581_FR1_PX_E102N27_0724_00333` | vehicle | 27 | missile |
| `852dc76a_D_0006` | Test2 | `852dc76a_DS_PHR1B_202003280350581_FR1_PX_E102N27_0724_00333` | vehicle | 6 | missile |
| `852dc76a_D_0009` | Test2 | `852dc76a_DS_PHR1B_202003280350581_FR1_PX_E102N27_0724_00333` | logistic | 35 | missile |
| `852dc76a_D_0011` | Test2 | `852dc76a_DS_PHR1B_202003280350581_FR1_PX_E102N27_0724_00333` | vehicle | 29 | missile |
| `852dc76a_D_0012` | Test2 | `852dc76a_DS_PHR1B_202003280350581_FR1_PX_E102N27_0724_00333` | vehicle | 31 | missile |
| `852dc76a_D_0014` | Test2 | `852dc76a_DS_PHR1B_202003280350581_FR1_PX_E102N27_0724_00333` | logistic | 36 | missile |
| `852dc76a_D_0019` | Test2 | `852dc76a_DS_PHR1B_202003280350581_FR1_PX_E102N27_0724_00333` | vehicle | 50 | missile |
| `852dc76a_D_0021` | Test2 | `852dc76a_DS_PHR1B_202003280350581_FR1_PX_E102N27_0724_00333` | vehicle | 7 | missile |
| `852dc76a_D_0022` | Test2 | `852dc76a_DS_PHR1B_202003280350581_FR1_PX_E102N27_0724_00333` | vehicle | 45 | missile |
| `852dc76a_D_0023` | Test2 | `852dc76a_DS_PHR1B_202003280350581_FR1_PX_E102N27_0724_00333` | vehicle | 48 | missile |
| `852dc76a_D_0025` | Test2 | `852dc76a_DS_PHR1B_202003280350581_FR1_PX_E102N27_0724_00333` | vehicle | 15 | missile |
| `852dc76a_D_0027` | Test2 | `852dc76a_DS_PHR1B_202003280350581_FR1_PX_E102N27_0724_00333` | vehicle | 5 | missile |
| `852dc76a_D_0028` | Test2 | `852dc76a_DS_PHR1B_202003280350581_FR1_PX_E102N27_0724_00333` | vehicle | 30 | missile |
| `d8bba13b_D_0000` | Test2 | `d8bba13b_DS_PHR1B_202109100317223_FR1_PX_E113N31_0818_00355` | vehicle | 30 | missile |
| `d8bba13b_D_0003` | Test2 | `d8bba13b_DS_PHR1B_202109100317223_FR1_PX_E113N31_0818_00355` | vehicle | 29 | missile |
| `d8bba13b_D_0005` | Test2 | `d8bba13b_DS_PHR1B_202109100317223_FR1_PX_E113N31_0818_00355` | vehicle | 0 | missile |
| `d8bba13b_D_0006` | Test2 | `d8bba13b_DS_PHR1B_202109100317223_FR1_PX_E113N31_0818_00355` | vehicle | 12 | missile |
| `d8bba13b_D_0007` | Test2 | `d8bba13b_DS_PHR1B_202109100317223_FR1_PX_E113N31_0818_00355` | vehicle | 9 | missile |
| `d8bba13b_D_0008` | Test2 | `d8bba13b_DS_PHR1B_202109100317223_FR1_PX_E113N31_0818_00355` | vehicle | 8 | missile |
| `d8bba13b_D_0009` | Test2 | `d8bba13b_DS_PHR1B_202109100317223_FR1_PX_E113N31_0818_00355` | vehicle | 33 | missile |
| `d8bba13b_D_0010` | Test2 | `d8bba13b_DS_PHR1B_202109100317223_FR1_PX_E113N31_0818_00355` | vehicle | 6 | missile |
| `d8bba13b_D_0011` | Test2 | `d8bba13b_DS_PHR1B_202109100317223_FR1_PX_E113N31_0818_00355` | vehicle | 14 | missile |
| `d8bba13b_D_0013` | Test2 | `d8bba13b_DS_PHR1B_202109100317223_FR1_PX_E113N31_0818_00355` | vehicle | 31 | missile |
| `d8bba13b_D_0015` | Test2 | `d8bba13b_DS_PHR1B_202109100317223_FR1_PX_E113N31_0818_00355` | camo | 7 | missile |
| `d8bba13b_D_0020` | Test2 | `d8bba13b_DS_PHR1B_202109100317223_FR1_PX_E113N31_0818_00355` | vehicle | 13 | missile |

### background → missile: 72

| Instance ID | Split | Scene | Raw GT class | GT index (0-based) | Model answer |
|---|---|---|---|---:|---|
| `18FEB10031_0040` | Test1 | `18FEB10031943-S3DS-200013190621_01_P001` | background | unmatched | missile |
| `18MAR10025_0007` | Test1 | `18MAR10025634-S3DS-200012866237_01_P001` | background | unmatched | missile |
| `19MAR13040_0030` | Test1 | `19MAR13040701-S3DS-200013268578_01_P001` | background | unmatched | missile |
| `19MAY10032_0018` | Test1 | `19MAY10032935-S3DS-200012352046_01_P001` | background | unmatched | missile |
| `19MAY10032_0026` | Test1 | `19MAY10032935-S3DS-200012352046_01_P001` | background | unmatched | missile |
| `19MAY10032_0038` | Test1 | `19MAY10032935-S3DS-200012352046_01_P001` | background | unmatched | missile |
| `19MAY10032_0040` | Test1 | `19MAY10032935-S3DS-200012352046_01_P001` | background | unmatched | missile |
| `19SEP16023_0081` | Test1 | `19SEP16023725-S3DS-200011883557_01_P001` | background | unmatched | missile |
| `19SEP16023_0090` | Test1 | `19SEP16023725-S3DS-200011883557_01_P001` | background | unmatched | missile |
| `19SEP16023_0137` | Test1 | `19SEP16023725-S3DS-200011883557_01_P001` | background | unmatched | missile |
| `19SEP16023_0147` | Test1 | `19SEP16023725-S3DS-200011883557_01_P001` | background | unmatched | missile |
| `19SEP16023_0149` | Test1 | `19SEP16023725-S3DS-200011883557_01_P001` | background | unmatched | missile |
| `21APR22040_0004` | Test1 | `21APR22040621-S3DS-200013119950_01_P001` | background | unmatched | missile |
| `21APR30054_0069` | Test1 | `21APR30054629-S3DS-200013142967_01_P001` | background | unmatched | missile |
| `21DEC12052_0056` | Test1 | `21DEC12052014-S3DS-200013142966_01_P001` | background | unmatched | missile |
| `21DEC12052_0075` | Test1 | `21DEC12052014-S3DS-200013142966_01_P001` | background | unmatched | missile |
| `21DEC12052_0091` | Test1 | `21DEC12052014-S3DS-200013142966_01_P001` | background | unmatched | missile |
| `21DEC27025_0017` | Test1 | `21DEC27025021-S3DS-200012895048_01_P001` | background | unmatched | missile |
| `21DEC27025_0028` | Test1 | `21DEC27025021-S3DS-200012895048_01_P001` | background | unmatched | missile |
| `21FEB15025_0001` | Test1 | `21FEB15025428-S3DS-200011883412_01_P001` | background | unmatched | missile |
| `21FEB15025_0006` | Test1 | `21FEB15025428-S3DS-200011883412_01_P001` | background | unmatched | missile |
| `21JAN25022_0032` | Test1 | `21JAN25022937-S3DS-200013104366_01_P001` | background | unmatched | missile |
| `21JAN25022_0033` | Test1 | `21JAN25022937-S3DS-200013104366_01_P001` | background | unmatched | missile |
| `22OCT24030_0044` | Test1 | `22OCT24030421-S3DS-200011896352_01_P001` | background | unmatched | missile |
| `22OCT24030_0078` | Test1 | `22OCT24030421-S3DS-200011896352_01_P001` | background | unmatched | missile |
| `23OCT24030_0020` | Test1 | `23OCT24030928-S3DS-200012400977_01_P001` | background | unmatched | missile |
| `23OCT24030_0026` | Test1 | `23OCT24030928-S3DS-200012400977_01_P001` | background | unmatched | missile |
| `24APR01051_0031` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | background | unmatched | missile |
| `24APR01051_0045` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | background | unmatched | missile |
| `24APR01051_0048` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | background | unmatched | missile |
| `24APR01051_0052` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | background | unmatched | missile |
| `24APR01051_0057` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | background | unmatched | missile |
| `24APR01051_0061` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | background | unmatched | missile |
| `24DEC21030_0006` | Test1 | `24DEC21030136-S3DS-200011913026_01_P001` | background | unmatched | missile |
| `24DEC21030_0020` | Test1 | `24DEC21030136-S3DS-200011913026_01_P001` | background | unmatched | missile |
| `24DEC21030_0021` | Test1 | `24DEC21030136-S3DS-200011913026_01_P001` | background | unmatched | missile |
| `24DEC21030_0022` | Test1 | `24DEC21030136-S3DS-200011913026_01_P001` | background | unmatched | missile |
| `24DEC21030_0023` | Test1 | `24DEC21030136-S3DS-200011913026_01_P001` | background | unmatched | missile |
| `24DEC21030_0024` | Test1 | `24DEC21030136-S3DS-200011913026_01_P001` | background | unmatched | missile |
| `24DEC21030_0025` | Test1 | `24DEC21030136-S3DS-200011913026_01_P001` | background | unmatched | missile |
| `24JAN04022_0068` | Test1 | `24JAN04022720-S3DS-200013055297_01_P001` | background | unmatched | missile |
| `24JAN04022_0073` | Test1 | `24JAN04022720-S3DS-200013055297_01_P001` | background | unmatched | missile |
| `24MAR27045_0023` | Test1 | `24MAR27045953-S3DS-200013168941_01_P001` | background | unmatched | missile |
| `26MAY09052_0030` | Test1 | `26MAY09052126-S3DS-200013142970_01_P001` | background | unmatched | missile |
| `20SEP27061_0009` | Test2 | `20SEP27061806-S3DS-200011619312_01_P001` | background | unmatched | missile |
| `21APR18030_0086` | Test2 | `21APR18030819-S3DS-200013545084_01_P001` | background | unmatched | missile |
| `21APR18030_0096` | Test2 | `21APR18030819-S3DS-200013545084_01_P001` | background | unmatched | missile |
| `22APR14045_0003` | Test2 | `22APR14045506-S3DS-200013368123_01_P001` | background | unmatched | missile |
| `22APR14045_0021` | Test2 | `22APR14045506-S3DS-200013368123_01_P001` | background | unmatched | missile |
| `22APR14045_0024` | Test2 | `22APR14045506-S3DS-200013368123_01_P001` | background | unmatched | missile |
| `22APR14045_0029` | Test2 | `22APR14045506-S3DS-200013368123_01_P001` | background | unmatched | missile |
| `22MAR07045_0151` | Test2 | `22MAR07045331-S3DS-200013349499_01_P001` | background | unmatched | missile |
| `234045af_D_0008` | Test2 | `234045af_DS_PHR1B_201808290337504_FR1_PX_E108N34_0924_00286` | background | unmatched | missile |
| `234045af_D_0018` | Test2 | `234045af_DS_PHR1B_201808290337504_FR1_PX_E108N34_0924_00286` | background | unmatched | missile |
| `234045af_D_0022` | Test2 | `234045af_DS_PHR1B_201808290337504_FR1_PX_E108N34_0924_00286` | background | unmatched | missile |
| `234045af_D_0024` | Test2 | `234045af_DS_PHR1B_201808290337504_FR1_PX_E108N34_0924_00286` | background | unmatched | missile |
| `234045af_D_0027` | Test2 | `234045af_DS_PHR1B_201808290337504_FR1_PX_E108N34_0924_00286` | background | unmatched | missile |
| `234045af_D_0029` | Test2 | `234045af_DS_PHR1B_201808290337504_FR1_PX_E108N34_0924_00286` | background | unmatched | missile |
| `23JAN10050_0013` | Test2 | `23JAN10050425-S3DS-200012483667_01_P001` | background | unmatched | missile |
| `23JAN15044_0539` | Test2 | `23JAN15044817-S3DS-200012483668_01_P001` | background | unmatched | missile |
| `23JAN15044_0553` | Test2 | `23JAN15044817-S3DS-200012483668_01_P001` | background | unmatched | missile |
| `23JAN15044_0563` | Test2 | `23JAN15044817-S3DS-200012483668_01_P001` | background | unmatched | missile |
| `23JAN15044_0565` | Test2 | `23JAN15044817-S3DS-200012483668_01_P001` | background | unmatched | missile |
| `23JAN15044_0575` | Test2 | `23JAN15044817-S3DS-200012483668_01_P001` | background | unmatched | missile |
| `23JAN15044_0590` | Test2 | `23JAN15044817-S3DS-200012483668_01_P001` | background | unmatched | missile |
| `23JAN15044_0601` | Test2 | `23JAN15044817-S3DS-200012483668_01_P001` | background | unmatched | missile |
| `23JAN15044_0620` | Test2 | `23JAN15044817-S3DS-200012483668_01_P001` | background | unmatched | missile |
| `24DEC24042_0011` | Test2 | `24DEC24042920-S3DS-200013378864_01_P001` | background | unmatched | missile |
| `24DEC24042_0013` | Test2 | `24DEC24042920-S3DS-200013378864_01_P001` | background | unmatched | missile |
| `25MAR23054_0022` | Test2 | `25MAR23054346-S3DS-200011078330_01_P001` | background | unmatched | missile |
| `26d44cd2_D_0047` | Test2 | `26d44cd2_DS_PHR1A_202012190354245_FR1_PX_E104N31_0306_00349` | background | unmatched | missile |
| `852dc76a_D_0026` | Test2 | `852dc76a_DS_PHR1B_202003280350581_FR1_PX_E102N27_0724_00333` | background | unmatched | missile |

### missile → radar: 6

| Instance ID | Split | Scene | Raw GT class | GT index (0-based) | Model answer |
|---|---|---|---|---:|---|
| `19DEC21034_0000` | Test1 | `19DEC21034631-S3DS-200013276864_01_P001` | missile | 3 | radar |
| `19MAR13040_0001` | Test1 | `19MAR13040701-S3DS-200013268578_01_P001` | missile | 2 | radar |
| `21DEC27025_0022` | Test1 | `21DEC27025021-S3DS-200012895048_01_P001` | missile | 17 | radar |
| `21FEB15025_0004` | Test1 | `21FEB15025428-S3DS-200011883412_01_P001` | missile | 3 | radar |
| `20SEP27061_0005` | Test2 | `20SEP27061806-S3DS-200011619312_01_P001` | missile | 2 | radar |
| `23MAY19062_0035` | Test2 | `23MAY19062258-S3DS-200011619589_01_P001` | missile | 0 | radar |

### missile → other: 66

| Instance ID | Split | Scene | Raw GT class | GT index (0-based) | Model answer |
|---|---|---|---|---:|---|
| `18MAR10025_0005` | Test1 | `18MAR10025634-S3DS-200012866237_01_P001` | missile | 9 | other |
| `19SEP16023_0003` | Test1 | `19SEP16023725-S3DS-200011883557_01_P001` | missile | 67 | other |
| `19SEP16023_0022` | Test1 | `19SEP16023725-S3DS-200011883557_01_P001` | missile | 62 | other |
| `19SEP16023_0076` | Test1 | `19SEP16023725-S3DS-200011883557_01_P001` | missile | 88 | other |
| `20NOV12043_0004` | Test1 | `20NOV12043850-S3DS-200012372799_01_P001` | missile | 7 | other |
| `20NOV12043_0005` | Test1 | `20NOV12043850-S3DS-200012372799_01_P001` | missile | 1 | other |
| `20NOV12043_0008` | Test1 | `20NOV12043850-S3DS-200012372799_01_P001` | missile | 27 | other |
| `20NOV12043_0014` | Test1 | `20NOV12043850-S3DS-200012372799_01_P001` | missile | 28 | other |
| `20NOV12043_0016` | Test1 | `20NOV12043850-S3DS-200012372799_01_P001` | missile | 26 | other |
| `21APR30054_0030` | Test1 | `21APR30054629-S3DS-200013142967_01_P001` | missile | 23 | other |
| `24APR01051_0001` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | missile | 3 | other |
| `24APR01051_0002` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | missile | 6 | other |
| `24APR01051_0003` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | missile | 27 | other |
| `24APR01051_0005` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | missile | 24 | other |
| `24APR01051_0006` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | missile | 0 | other |
| `24APR01051_0008` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | missile | 25 | other |
| `24APR01051_0010` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | missile | 21 | other |
| `24APR01051_0011` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | missile | 5 | other |
| `24APR01051_0012` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | missile | 4 | other |
| `24APR01051_0013` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | missile | 7 | other |
| `24APR01051_0014` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | missile | 2 | other |
| `24APR01051_0015` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | missile | 18 | other |
| `24APR01051_0017` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | missile | 28 | other |
| `24APR01051_0018` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | missile | 22 | other |
| `24APR01051_0020` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | missile | 23 | other |
| `24APR01051_0021` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | missile | 20 | other |
| `24APR01051_0029` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | missile | 33 | other |
| `24APR01051_0032` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | missile | 19 | other |
| `24APR01051_0035` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | missile | 35 | other |
| `24APR01051_0038` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | missile | 34 | other |
| `24APR01051_0042` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | missile | 16 | other |
| `24APR01051_0043` | Test1 | `24APR01051503-S3DS-200012320748_01_P001` | missile | 17 | other |
| `24JAN04022_0016` | Test1 | `24JAN04022720-S3DS-200013055297_01_P001` | missile | 10 | other |
| `24JAN04022_0022` | Test1 | `24JAN04022720-S3DS-200013055297_01_P001` | missile | 7 | other |
| `24JAN04022_0040` | Test1 | `24JAN04022720-S3DS-200013055297_01_P001` | missile | 5 | other |
| `24JAN04022_0044` | Test1 | `24JAN04022720-S3DS-200013055297_01_P001` | missile | 4 | other |
| `24JAN04022_0050` | Test1 | `24JAN04022720-S3DS-200013055297_01_P001` | missile | 6 | other |
| `24JAN04022_0051` | Test1 | `24JAN04022720-S3DS-200013055297_01_P001` | missile | 1 | other |
| `24JAN04022_0075` | Test1 | `24JAN04022720-S3DS-200013055297_01_P001` | missile | 9 | other |
| `24JAN04022_0077` | Test1 | `24JAN04022720-S3DS-200013055297_01_P001` | missile | 8 | other |
| `24MAR27045_0002` | Test1 | `24MAR27045953-S3DS-200013168941_01_P001` | missile | 10 | other |
| `24MAR27045_0009` | Test1 | `24MAR27045953-S3DS-200013168941_01_P001` | missile | 2 | other |
| `20SEP27061_0010` | Test2 | `20SEP27061806-S3DS-200011619312_01_P001` | missile | 1 | other |
| `20SEP27061_0012` | Test2 | `20SEP27061806-S3DS-200011619312_01_P001` | missile | 3 | other |
| `22MAR02025_0004` | Test2 | `22MAR02025946-S3DS-200012804518_01_P001` | missile | 12 | other |
| `22MAR02025_0006` | Test2 | `22MAR02025946-S3DS-200012804518_01_P001` | missile | 6 | other |
| `22MAR02025_0016` | Test2 | `22MAR02025946-S3DS-200012804518_01_P001` | missile | 15 | other |
| `22MAR02025_0019` | Test2 | `22MAR02025946-S3DS-200012804518_01_P001` | missile | 7 | other |
| `22MAR02025_0033` | Test2 | `22MAR02025946-S3DS-200012804518_01_P001` | missile | 2 | other |
| `22MAR02025_0039` | Test2 | `22MAR02025946-S3DS-200012804518_01_P001` | missile | 16 | other |
| `22MAR02025_0040` | Test2 | `22MAR02025946-S3DS-200012804518_01_P001` | missile | 13 | other |
| `22MAR02025_0044` | Test2 | `22MAR02025946-S3DS-200012804518_01_P001` | missile | 1 | other |
| `22MAR02025_0064` | Test2 | `22MAR02025946-S3DS-200012804518_01_P001` | missile | 8 | other |
| `22MAR02025_0085` | Test2 | `22MAR02025946-S3DS-200012804518_01_P001` | missile | 5 | other |
| `22MAR07045_0002` | Test2 | `22MAR07045331-S3DS-200013349499_01_P001` | missile | 126 | other |
| `22MAR07045_0003` | Test2 | `22MAR07045331-S3DS-200013349499_01_P001` | missile | 124 | other |
| `22MAR07045_0012` | Test2 | `22MAR07045331-S3DS-200013349499_01_P001` | missile | 129 | other |
| `22MAR07045_0016` | Test2 | `22MAR07045331-S3DS-200013349499_01_P001` | missile | 147 | other |
| `22MAR07045_0033` | Test2 | `22MAR07045331-S3DS-200013349499_01_P001` | missile | 123 | other |
| `22MAR07045_0045` | Test2 | `22MAR07045331-S3DS-200013349499_01_P001` | missile | 132 | other |
| `22MAR07045_0101` | Test2 | `22MAR07045331-S3DS-200013349499_01_P001` | missile | 128 | other |
| `22MAR07045_0123` | Test2 | `22MAR07045331-S3DS-200013349499_01_P001` | missile | 133 | other |
| `23MAY19062_0020` | Test2 | `23MAY19062258-S3DS-200011619589_01_P001` | missile | 2 | other |
| `23MAY19062_0038` | Test2 | `23MAY19062258-S3DS-200011619589_01_P001` | missile | 4 | other |
| `23MAY19062_0089` | Test2 | `23MAY19062258-S3DS-200011619589_01_P001` | missile | 3 | other |
| `26d44cd2_D_0018` | Test2 | `26d44cd2_DS_PHR1A_202012190354245_FR1_PX_E104N31_0306_00349` | missile | 12 | other |

### missile → background: 9

| Instance ID | Split | Scene | Raw GT class | GT index (0-based) | Model answer |
|---|---|---|---|---:|---|
| `22MAR07045_0008` | Test2 | `22MAR07045331-S3DS-200013349499_01_P001` | missile | 130 | background |
| `22MAR07045_0010` | Test2 | `22MAR07045331-S3DS-200013349499_01_P001` | missile | 131 | background |
| `22MAR07045_0019` | Test2 | `22MAR07045331-S3DS-200013349499_01_P001` | missile | 146 | background |
| `22MAR07045_0020` | Test2 | `22MAR07045331-S3DS-200013349499_01_P001` | missile | 125 | background |
| `22MAR07045_0025` | Test2 | `22MAR07045331-S3DS-200013349499_01_P001` | missile | 141 | background |
| `22MAR07045_0028` | Test2 | `22MAR07045331-S3DS-200013349499_01_P001` | missile | 148 | background |
| `22MAR07045_0039` | Test2 | `22MAR07045331-S3DS-200013349499_01_P001` | missile | 127 | background |
| `22MAR07045_0071` | Test2 | `22MAR07045331-S3DS-200013349499_01_P001` | missile | 142 | background |
| `22MAR07045_0086` | Test2 | `22MAR07045331-S3DS-200013349499_01_P001` | missile | 149 | background |


