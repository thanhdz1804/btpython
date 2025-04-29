# BAITAPTAP THUCHANH PYTHON
Bài tập thực hành python
Bài 1: 
Thực hiện lấy dữ liệu thời tiết từ url sau: https://www.pokemon.com/us/api/pokedex/kalos
Yêu cầu:
+ Lấy thông tin dữ liệu các trường: number, height, weight, name, type, ThumbnailImage và lưu vào một file .csv
+ Dựa vào dữ liệu đã lấy được đó. Hãy thực hiện lấy thông tin của các Pokemon có type là poison

Bài 2:
Lấy dữ liệu từ file excel từ link: https://docs.google.com/spreadsheets/d/1BnOzoEG0s6c8MpiUANZ0_pawXNHqdkid/edit?usp=sharing&ouid=115874127894901285908&rtpof=true&sd=true

Hãy thực hiện lọc dữ liệu của các dữ liệu với điều kiện sau:
- Trường dữ liệu có cột vpv2 và pDisCharge có giá trị chẵn, cột prec lẻ lưu vào trong file mới có tên: Data_new.csv
- Thực hiện tính tổng dữ liệu của từng hàng vBus1, vBus2, tạo một cột mới có tên Sum_vBUS và ghi kết quả vào đó.

Bài 3: 
Tạo một chương trình quản lý nhà để xe, sử dụng OOP với các lớp như: Info_Xe, Money_Time.
(Info_Xe sẽ chứa một số trường thông tin như: Loại xe (Xe đạp, xe máy, xe điện, ô tô, ...), chủ xe, thời gian gửi xe (tính theo giờ), biển số xe (Nếu có). Money_Time bao gồm: Giá tiền của từng xe trong 1 giờ. Quy định: Xe đạp: 2k/giờ, Xe máy: 5k/giờ, Xe điện: 3.5k/giờ, ô tô: 10k/giờ)
Yêu cầu: 
- Hệ thống cho phép thêm, sửa, xóa thông tin, cập nhật thông tin của Info_Xe hoặc Money_Time.
- Tính toán giá thành gửi xe của từng người, xuất thông tin những người đã gửi xe trên 20k
- Ghi dữ liệu vào trong file excel
## BAI1
![image](https://github.com/user-attachments/assets/0b7b0191-47fd-401e-a8b1-08adcdb56bcf)
import requests: requests: dùng để gửi yêu cầu HTTP và lấy dữ liệu từ Internet.
import csv : csv: dùng để làm việc với file CSV (ghi, đọc...).
url = "https://gist.githubusercontent.com/yi-jia.../raw/79ddabce..."     : Đây là URL chứa dữ liệu dạng JSON về các Pokémon.
response = requests.get(url) : requests.get(url): gửi yêu cầu GET đến URL.
data = response.json() : json(): chuyển dữ liệu trả về (dạng JSON) thành kiểu dữ liệu Python (danh sách các dict).
fields = ["number", "name", "type", "height", "weight", "ThumbnailImage"] : Đây là các trường sẽ được trích từ mỗi Pokémon để lưu vào CSV
with open("pokemon_data.csv", mode="w", newline="", encoding="utf-8") as file: Mở file CSV với chế độ ghi ("w"), xóa nội dung cũ nếu có.
    writer = csv.DictWriter(file, fieldnames=fields)
    writer.writeheader() : Mở file CSV với chế độ ghi ("w"), xóa nội dung cũ nếu có.
    for pokemon in data: writeheader(): ghi dòng tiêu đề (tên các cột). ới mỗi Pokémon trong data, lấy giá trị của từng trường trong fields và ghi vào một dòng của file CSV.
        row = {field: pokemon.get(field) for field in fields}
        writer.writerow(row)
  print("Dữ liệu đã được lưu vào 'pokemon_data.csv'") :In ra thông báo khi hoàn tất lưu dữ liệu.
![image](https://github.com/user-attachments/assets/c327f56d-f16a-4668-8215-58b9fcf93e00)
  pandas (viết tắt là pd) là thư viện mạnh để xử lý dữ liệu dạng bảng (DataFrame).
ast.literal_eval() dùng để chuyển chuỗi biểu diễn danh sách (vd: "['grass', 'poison']") thành list Python thực sự.
Tải toàn bộ nội dung từ pokemon_data.csv vào một DataFrame có tên df.
Vì dữ liệu trong file CSV có thể lưu ["grass", "poison"] dưới dạng chuỗi, bạn dùng ast.literal_eval() để chuyển về list thực.
Kiểm tra nếu là chuỗi và bắt đầu bằng "[" thì mới chuyển đổi, còn lại sẽ để nguyên dưới dạng danh sách có một phần tử.
Với mỗi dòng trong df, biến x là danh sách các loại (vd: ['Grass', 'Poison']).
Dùng list comprehension để chuyển từng loại về chữ thường (lowercase), rồi kiểm tra nếu 'poison' có trong đó.
print("Các Pokémon có loại 'poison':")
print(poison_pokemon[["number", "name", "type"]])In tiêu đề. In bảng gồm các cột number, name, type của các Pokémon loại poison.
## kết quả 
![image](https://github.com/user-attachments/assets/e37b5872-e1e4-4528-a296-f7dc6033efa0)
![image](https://github.com/user-attachments/assets/e9a89c56-cf1d-4cfa-b62a-a9363f49d170)
## bai 2 



