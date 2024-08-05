# Chuẩn bị dataset

We have conducted experiments on various datasets. A notable example is the "Celegans Genetic Multiplex" dataset. This dataset stores information on genetic and protein interactions from both humans and organisms. It comprises 3879 nodes each labeled with an integer ID ranging from 1 to 3879 and a total of 8181 connections. Các file dữ liệu có cấu trúc như sau:

The multiplex is directed and unweighted stored as edges list in the file `celegans_genetic_multiplex.edges`

| layerID | nodeID | nodeID | weight |
|---------|--------|--------|--------|
| 1       | 1      | 2      | 1      |
| 1       | 1      | 3      | 1      |
| 1       | 3      | 824    | 1      |
| ...     | ...    | ...    | ...    |

The IDs of all layers are stored in `celegans_genetic_layers.txt`

| layerID | layerLabel                                           |
|---------|------------------------------------------------------|
| 1       | direct_interation                                    |
| 2       | physical_association                                 |
| 3       | additive_genetic_interaction_defined_by_inequality   |
| 4       | suppressive_genetic_interaction_defined_by_inequality|
| 5       | association                                          |
| 6       | colocalization                                       |

The IDs of nodes together with their name can be found in the file `celegans_genetic_nodes.txt`

| nodeID | nodeLabel  |
|--------|------------|
| 1      | soc-2      |
| 2      | W07G04.5   |
| ...    | ...        |

## Tiền xử lý data

- Chạy file: `createDataset.py`.
Các bước như sau:
- Chuyển data thô về dạng graph.
- Chuẩn bị các tập seed set mẫu để thực hiện mô phỏng trên các mô hình lan truyền thông tin như IC hoặc LT. Các mẫu dữ liệu và kết quả mô phỏng sẽ được sử dụng làm đầu vào cho framework EMIM hỗ trợ việc xác định tập seed set tối ưu. Dữ liệu lưu trong file `Celegans_mean_LT10.SG`

Cấu trúc của file như sau:
- Cột seed node: mỗi hàng tương ứng với một node trong đồ thị nó chứa giá trị 1 hoặc 0 với giá trị 1 biểu thị node thuộc seed set và giá trị 0 ngược lại.
- Cột 2: infection probability of each node.

| Seed node | Infection probability |
|-----------|-----------------------|
| 1         | 1                     |
| 0         | 0.2                   |
| 0         | 0                     |
| 1         | 1                     |
| ...       | ...                   |
