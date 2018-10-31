# Spatial Analysis for the Selection of Locations of Multi-storey Central Parking in Surabaya

#### Cahya Putra Hikmawan - 05111540000119

##### Best Documentation on https://github.com/cphikmawan/geographic-information-system-courses

### Contents
[1. Materials](#1-materials)

[2. Load Vector Data](#2-load-vector-data)

[3. Install Plugins and Create Buffer](#3-install-plugins-and-create-buffer)

[4. Union Each Buffer](#4-union-each-buffer)

[5. Clip Buffer](#5-clip-buffer)

### 1. Materials
- **Vector Data That Needed**
[Here The Vector Data](assets/material/)

### 2. Load Vector Data
#### Step 1 - Drag and drop or load the vector data to **_layers_**
![load-vector](assets/img/load-vector.png)

### 3. Install Plugins and Create Buffer
#### Step 1 - Install **Multi-distance Buffer**
- In the **menu** select plugins
- Type **_search_** **multi-distance buffer**
- Then **install** plugins
![install-plugins](assets/img/install-plugins.png)

#### Step 2 - Create Buffer
- Make Decision Value For Each Vector Data
    1. Rapat Bangunan

    | Area Cakupan | Skor |
    | --- | --- |
    | 100 Meter | 1 |
    | 250 Meter | 2 |
    | 500 Meter | 3 |

    2. Kepadatan

    | Kepadatan(jumlah penduduk) | Skor |
    | --- | --- |
    | 100 | 1 |
    | 250 | 2 |
    | 500 | 3 |

    3. Transportasi

    | Area Cakupan | Skor |
    | --- | --- |
    | 200 Meter | 1 |
    | 100 Meter | 2 |
    | 50 Meter | 3 |

    4. Belanja

    | Area Cakupan | Skor |
    | --- | --- |
    | 200 Meter | 1 |
    | 100 Meter | 2 |
    | 50 Meter | 3 |

    5. Jalan

    | Area Cakupan | Skor |
    | --- | --- |
    | 200 Meter | 1 |
    | 100 Meter | 2 |
    | 50 Meter | 3 |

- **Create** The Buffer Each Buffer

    Example: Create Jalan Buffer
    1. Open Multi-Distance Buffer
        ![open-plugins](assets/img/open-plugins.png)
    2. Select Layer -> Add Value -> Ok -> Close
        ![fill-value](assets/img/fill-value.png)
    3. The Result
        ![the-result](assets/img/jalan-buffer.png)

- After create buffer and get **result** like this
    ![the-result-buffer](assets/img/the-result-buffer.png)

- Then **Edit** Score Value

    Example: Edit Score Value on Jalan Buffer
    1. **Right Click** on The Buffer -> **Open Attribute Table**
        ![open-table](assets/img/open-table.png)
    2. **Toggle Editing Mode** (Click on Pencil Icon)

        - **Delete Inner Column**

            ![delete-inner](assets/img/delete-inner.png)

        - **Add Score Column and Add the Value**

            ![add-score](assets/img/add-score.png)


>**Dont forget to save each created buffer**

### 4. Union Each Buffer

- On The **Menu** select **_Processing_** -> **_Toolbox_**
- Search **union**

#### Step 1 - Union Buffer *Rapat Bangunan & Kepadatan*
![union-1](assets/img/union1.png)

#### Step 2 - Union Buffer Pada *Step 1 & Buffer Jalan*
![union-2](assets/img/union2.png)

#### Step 3 - Union Buffer Pada *Step 2 & Buffer Transportasi*
![union-3](assets/img/union3.png)

#### Step 4 - Union Buffer Pada *Step 3 & Buffer Belanja*
![union-4](assets/img/union4.png)

#### Step 5 - *Open* Attribute Table -> *Edit* empty field with *"0"* Value
![open-table2](assets/img/open-table2.png)

#### Step 6 - *Open* Calculator
![calculator](assets/img/calculator.png)

1. Fill **output field name**
2. Then Choose **fields and values**
3. Then Double Click on **score**
4. Click **Plus Notation "+"**
5. And click **score_2**, then repeat until **score_5**.

6. It will look like this.

    ![calculator2](assets/img/calculator2.png)

7. Ok. it will create column named **total**

    ![calculator-result](assets/img/calculator-result.png)


#### Step 5 - Set the Color

1. Right Click -> **Properties**
2. Edit from **Single Symbol** to **Categorized**
3. Select column to **total**
4. Optional (Select Symbol) -> Im not doing this
5. Select **color ramp** for gradation color

![properties](assets/img/properties.png)

#### Union Result
- Total Screenshot

![union-result-total](assets/img/union-result-total.png)

- Zoom In Screenshot

![union-result](assets/img/result-union.png)

### 5. Clip Buffer

> **Because the union buffer offside from the base layer (kabupaten),**
> **We need to Clip the Union Buffer**
- On The **Menu** select **_Processing_** -> **_Toolbox_**
- Search **clip**

![clip](assets/img/clip.png)

**1. Input Layer -> union layer from all buffer**

**2. Overlay Layer -> The main layer (kabupaten)**

**3. Clipped -> Save Clip**

**4. Run**

![clipped](assets/img/clipped.png)

### Conclusion

![conclusion](assets/img/conclusion.png)

| Value | Rate |
| --- | --- |
| 1 - 3 | Bad |
| 4 - 6 | Common |
| 7 - 9 | Enaugh |
| 10 - 11 | Best |

###### Created with <3 by Cloudy