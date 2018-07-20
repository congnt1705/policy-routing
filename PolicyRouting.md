# Policy Routing Theory
Policy Routing cung cấp khả năng định tuyến dựa trên bất kỳ các trường nào của 1 gói tin. Policy Routing là một bộ các quy tắc thực hiện cấu trúc định tuyến của một mạng.  
**Address**	xác định vị trí của service  
**Route**	xác định vị trí của address  
**Rule**	xác định vị trí của route  

# Routing Policy Database (RPDB)
RPdB kiểm soát thứ tự các rule mà kernel sẽ tìm kiếm trong bảng định tuyến. Khi một gói tin đến router để định tuyến, kernel sẽ bắt đầu tìm kiếm rule có priority thấp nhất, nếu có bất kỳ rule nào phù hợp với gói tin, kernel sẽ thực hiện định tuyến theo rule đó. RPDB mặc định sẽ có 3 rule:  
- **Priority 0: lookup local**: là bảng định tuyến đặc biệt chứa các tuyến có ưu tiên cao cho local và broadcast address.  
- **Priority 32766: lookup main**: là bảng định tuyến thông thường.  
- **Priority 32767: lookup default**: bảng này rỗng và được dành cho quá trình xử lý sau này nếu các quy tắc mặc định trước đó không chọn được gói.  

RPDB có thể chứa các rule sau:  
- **unicast:** tham chiếu đến bảng định tuyến đã chỉ định trong rule.  
- **nat:** NAT địa chỉ nguồn sang địa chỉ IP khác.  
- **blackhole** Drop gói tin.  
- **unreachable:** tạo ra gói ICMP unreachable đến source của gói.  
- **prohibit:** Rule tạo ra gói ICMP prohibit (bị cấm) đối với source của gói.  

