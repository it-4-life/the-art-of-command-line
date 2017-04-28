🌍
*[Čeština](README-cs.md) ∙ [Deutsch](README-de.md) ∙ [Ελληνικά](README-el.md) ∙ [English](README.md) ∙ [Español](README-es.md) ∙ [Français](README-fr.md) ∙ [Indonesia](README-id.md) ∙ [Italiano](README-it.md) ∙ [日本語](README-ja.md) ∙ [한국어](README-ko.md) ∙ [Português](README-pt.md) ∙ [Română](README-ro.md) ∙ [Русский](README-ru.md) ∙ [Slovenščina](README-sl.md) ∙ [Українська](README-uk.md) ∙ [简体中文](README-zh.md) ∙ [繁體中文](README-zh-Hant.md) ∙ [Tiếng Việt](README-vi.md)*


# The Art of Command Line

[![Ask a Question](https://img.shields.io/badge/%3f-Ask%20a%20Question-ff69b4.svg)](https://airtable.com/shrzMhx00YiIVAWJg)

[![Join the chat at https://gitter.im/jlevy/the-art-of-command-line](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/jlevy/the-art-of-command-line?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)


- [Meta](#meta)
- [Basics](#basics)
- [Everyday use](#everyday-use)
- [Processing files and data](#processing-files-and-data)
- [System debugging](#system-debugging)
- [One-liners](#one-liners)
- [Obscure but useful](#obscure-but-useful)
- [OS X only](#os-x-only)
- [Windows only](#windows-only)
- [More resources](#more-resources)
- [Disclaimer](#disclaimer)


![curl -s 'https://raw.githubusercontent.com/jlevy/the-art-of-command-line/master/README.md' | egrep -o '`\w+`' | tr -d '`' | cowsay -W50](cowsay.png)

Command line là một kỹ năng thường bị bỏ quên hoặc được xem là phức tạp, nhưng nếu thành thạo, nó sẽ giúp bạn tăng tính linh hoạt và năng suất làm việc lên rất nhiều. Bài viết này là một tập hợp các ghi chú và mẹo khi sử dụng command line mà chúng tôi thấy nó rất hữu ích khi làm việc trên Linux. Bài viết này không dài, nhưng nếu bạn có thể nhớ và sử dụng tất cả các ghi chú ở đây, bạn sẽ biết được rất nhiều thứ.

Bài viết này được thực hiện bởi [nhiều tác giả và người dịch](AUTHORS.md).
Một số phần ở đây
[ban đầu](http://www.quora.com/What-are-some-lesser-known-but-useful-Unix-commands)
[xuất hiện](http://www.quora.com/What-are-the-most-useful-Swiss-army-knife-one-liners-on-Unix)
trên [Quora](http://www.quora.com/What-are-some-time-saving-tips-that-every-Linux-user-should-know),
nhưng nó đã được di chuyển sang Github và đã được cải thiện rất nhiều.
Hãy [**gửi câu hỏi**](https://airtable.com/shrzMhx00YiIVAWJg) nếu bạn có bất cứ câu hỏi nào liên quan đến command line. Hoặc [**đóng góp**](/CONTRIBUTING.md) nếu bạn muốn cải thiện bài viết!

## Meta

Phạm vi:

- Hướng dẫn này dành cho cả những người mới bắt đầu hoặc đã có kinh nghiệm. Mục đích của bài viết là *theo chiều rộng* (mọi thứ đều quan trọng), *tính cụ thể*(đưa ra các ví dụ cụ thể cho trường hợp thông thường nhất) và *ngắn gọn* (tránh những thứ không cần thiết hoặc có thể tìm kiếm dễ dàng ở nơi khác). Các ghi chú ở đây đều là thiết yếu trong một số trường hợp hoặc sẽ tiết kiệm thời gian đáng kể so với các phương pháp khác.
- Bài viết được viết cho Linux, với ngoại lệ trong phần "[OS X only](#os-x-only)" và "[Windows only](#windows-only)". Nhiều phần khác có thể được áp dụng hoặc cài đặt cho các hệ thống Unix khác hoặc OSX (hoặc thậm chí là Cygwin).
- Bài viết tập trung vào việc thao tác trực tiếp với Bash, cũng có những mẹo áp dụng cho các shell khác và mẹo để lập trình Bash.
- Bài viết bao gồm cả những lệnh Unix "tiêu chuẩn" cũng như các lệnh đặc biệt yêu cầu phải cài đặt package -- miễn là nó đủ quan trọng được thêm vào.

Ghi chú:

- Để giữ bài viết trong 1 trang, nội dung được thêm vào bằng cách tham chiếu đến các tài liệu khác. Bạn đủ thông minh để tìm kiếm hướng dẫn chi tiết ở nơi khác một khi bạn đã nắm được ý tưởng thực hiện. Sử dụng `apt-get`, `yum`, `dnf`, `pacman`, `pip` or `brew` (tuỳ theo hệ thống) để cài đặt các chương trình.
- Sử dụng [Explainshell](http://explainshell.com/) để xem các trợ giúp hữu ích về các phần trong câu lệnh, các tuỳ chọn, các chuyển hướng nhập xuất,...

## Basics

- Học cơ bản về Bash. Trên thực tế, bạn có thể gõ `man bash` và ít nhất là lướt qua toàn bộ trang hướng dẫn, nó không dài và rất dễ theo dõi. Những shell khác có thể hấp dẫn hơn, nhưng bản thân Bash đã rất mạnh và luôn có sẵn vì Bash được cài đặt mặc định trên hầu hết các distro Linux (những shell khác như zsh, fish shell,... có thể rất thú vị nhưng thường không được cài đặt sẵn).

- Học cách sử dụng ít nhất một text editor trên command line, lý tưởng là Vim (`vi`).

- Biết cách đọc tài liệu với lệnh `man` (lệnh `man man` liệt kê danh sách các mục tài liệu từng nhóm, ví dụ nhóm 1 là các chương trình thực thi và câu lệnh thông thường, nhóm 5 là chỉ dẫn về các file cấu hình (vd xem chỉ dẫn về cấu hình file `/ets/passwd` => `man 5 passwd`, cấu hình file `/etc/hosts` => `man 5 hosts`,...), nhóm 8 là nhóm các tài liệu về quản trị hệ thống...). Tìm kiếm các trang `man` bằng câu lệnh `apropos <keyword>`. Có một số câu lệnh không phải là file thực thi mà là các keyword hoặc lệnh builtin được cung cấp bởi Bash, bạn có thể xem trợ giúp về các lệnh đó với `help` và `help -d`. Bạn có thể kiểm tra 1 câu lệnh là file thực thi hay shell builtin hay là 1 alias bằng lệnh `type <command>`.

- Tìm hiểu về chuyển hướng nhập xuất bằng các ký tự `>`, `<` và `|`. Biết được `>` sẽ ghi đè file output còn `>>` sẽ ghi append vào file output. Tìm hiểu về stdout, stderr.

- Tìm hiểu về sử dụng `glob` trong file name (được hiểu là việc sử dụng các ký tự đại diện wildcard khi làm việc với tên file trên command line), các ký tự thông dụng là `*` (hoặc `?`, `[`...`]`) và dấu nháy. Hiểu sự khác biệt giữa dấu nháy đơn `'` và dấu nháy kép `"`.

- Làm quen với việc quản lý các job, tiến trình trong Bash: `&`, **ctrl-z**, **ctrl-c**, `jobs`, `fg`, `bg`, `kill`,...

- Biết `ssh` và cơ bản về xác thực không cần mật khẩu `ssh-agent`, `ssh-add`,...

- Biết cách quản lý file: `ls`, `ls -l` (hiểu được mỗi cột trong kết quả `ls -l` có ý nghĩa gì), `less`, `head`, `tail` và `tail -f` (`less +F`), `ln`, `ln -s` (khác biệt giữa hard link và soft link là gì?), `chown`, `chmod`, `du`. Về quản lý filesystem, phân vùng, sử dụng `df`, `mount`, `fdisk`, `mkfs`, `lsblk`. Hiểu về inode `ls -i` hoặc `df -i`.

- Quản lý network: `ip` hoặc `ifconfig`, `dig`, `traceroute`, `route`.

- Học cách sử dụng các hệ thống quản lý mã nguồn, chẳng hạn `git`.

- Nắm vững về biểu thức chính quy regex và các tuỳ chọn của lệnh `grep`/`egrep`: `-i`, `-o`, `-v`, `-A`, `-B` và `-C`

- Biết cách sử dụng `apt-get`, `yum`, `dnf` hoặc `pacman` (tuỳ thuộc vào distro) để tìm kiếm và cài đặt packages. Một số package được viết bằng Python dưới đây có thể được cài đặt dễ dàng hơn bằng cách sử dụng `pip`.


## Everyday use

- Trong Bash, sử dụng phím **Tab** để tự động điền các câu lệnh hoặc tuỳ chọn của câu lệnh, **ctrl-r** để tìm kiếm lịch sử sử dụng lệnh.

- Với Bash, sử dụng **ctrl-w** để xoá từ cuối cùng trong câu lệnh, **ctrl-u** để xoá nội dung câu lệnh từ vị trí con trỏ đến đầu dòng, **ctrl-y** đến dán vừa bị xoá bởi **ctrl-u**. Sử dụng **alt-b** và **alt-f** để di chuyển giữa các từ, **ctrl-a** để di chuyển con trỏ về đầu dòng, **ctrl-e** để di chuyển con trỏ xuống cuối dòng, **ctrl-k** để xoá nội dung từ vị trí con trỏ đến cuối dòng, **ctrl-l** để xoá màn hình. Xem `man readline` để biết các phím tắt khác.

- Nếu bạn thích các phím tắt theo kiểu `vi` sử dụng `set -o vi` (và `set -o emacs` để quay về mặc định).

- Để sửa các câu lệnh dài, sau khi đã thiết lập editor (ví dụ `export EDITOR=vim`), tổ hợp phím **ctrl-x** **ctrl-e** sẽ mở editor với nội dung là câu lệnh hiện tại, bạn có thể thao tác với câu lệnh trên nhiều dòng. Nếu sử dụng phím tắt kiểu `vi`, dùng tổ hợp phím **esc-v**

 - Xem các câu lệnh gần đây, sử dùng `history`. Sử dụng `!n` (trong đó `n` là số của câu lệnh trong danh sách history) để chạy lại lệnh, `!$` để lấy tham số cuối cùng trong câu lệnh trước, `!!` để lấy câu lệnh trước đó (xem "HISTORY EXPANSION" trong man `man bash`).

- Di chuyển đến thư mục home với `cd`. Truy cập vào các file bên trong thư mục home với tiền tố `~` (vd: `~/.bashrc`). Nó cũng giống như sử dụng biến `$HOME` khi viết shell scripts.

- Di chuyển về thư mục làm việc trước đó: `cd -`.

- Nếu bạn đang gõ lệnh nhưng bạn thay đổi suy nghĩ và không muốn chạy lệnh đó nữa, bạn có thể comment dòng lệnh đó bằng cách thêm dấu `#` ở đầu dòng (sử dụng tổ hợp phím **ctrl-a** **#** **enter**). Bạn có thể sử dụng câu lệnh đó lúc khác thông qua lịch sử.

- Sử dụng `xargs` (hoặc `parallel`). Nó rất mạnh mẽ. Nếu bạn không chắc nó sẽ làm đúng yêu cầu của bạn, bạn có thể dùng `xargs echo` trước. Tùy chọn `-I{}` cũng rất tiện dụng.
```bash
    find . -name '*.py' | xargs grep some_function
    cat hosts | xargs -I{} ssh root@{} hostname
```

- `pstree -p` dùng để hiển thị các tiến trình hệ thống theo dạng cây.

- Sử dụng `pgrep` và `pkill` để tìm kiếm hoặc truyền signal cho các tiến trình theo tên (`-f` cũng rất có ích).

- Biết các loại signal có thể truyền cho các tiến trình. Ví dụ, để tạm dưng 1 tiếng trình, sử dụng `kill -STOP [pid]`. Để xem danh sách đầy đủ, xem `man 7 signal`.

- Sử dụng `nohup` hoặc `disown` nếu bạn muốn giữ 1 tiến trình chạy nền.

- Kiểm tra các tiến trình đang lắng nghe trên cổng TCP nào, sử dụng `netstat -lntp` hoặc `ss -plat` (tùy chọn `-u` để kiểm tra cho UDP).

- Xem thêm `lsof` và `fuser` cho việc mở socket và files.

- Sử dụng `uptime` hoặc `w` để biết thời gian chạy của hệ thống.

- Sử dụng `alias` để tạo lệnh tắt cho các câu lệnh hay dùng. Ví dụ, `alias ll='ls -latr'`.

- Lưu các alias, các cài đặt shell, và các hàm thường dùng trong `~/.bashrc`, và [sắp xếp các file cấu hình](http://superuser.com/a/183980/7106) để các cài đặt được áp dụng cho tất cả các shell.

- Để các cài đặt về biến môi trường cũng như các câu lệnh cần được chạy khi bạn login trong `~/.bash_profile`.

- Đồng bộ các file cấu hình (vd: `.bashrc`, `.bash_profile`,...) giữa các máy tính bằng Git.

- Cần chú ý khi sử dụng tên biến, tên file có chứa dấu cách. Bao quanh tên biến trong Bash bởi dấu ngoặc kép, vd: `"$FOO"`. Thêm tùy chọn `-0` hoặc `-print0` để sử dụng ký tự ASCII NUL làm phân tách giữa các tên file thay vì dấu cách, vd: `locate -0 pattern | xargs -0 ls -al` hoặc `find / -print0 -type d | xargs -0 ls -al`. Để lặp qua danh sách tên file có chứa dấu cách, đặt giá trị của biến `IFS` là newline `IFS=$'\n'`.

- Trong Bash scripts, `set -x` (hoặc `set -v`) để debug output. Sử dụng strict mode trừ khi bạn có lý do đặc biệt: `set -e` để dừng script khi gặp lỗi (exit code khác 0), `set -u` để phát hiện các biến chưa được khởi tạo. Cũng lưu ý thêm `set -o pipefail` để dừng script khi có lỗi khi pipe. Với các script phức tạp hơn, sử dụng `trap` khi EXIT hoặc ERR. Một thói quen tốt khi bắt đầu 1 script theo cách sau, nó sẽ phát hiện và dừng khi có lỗi xảy ra và hiện thông báo:
```bash
    set -euo pipefail
    trap "echo 'error: Script failed: see failed command above'" ERR
```

- Trong Bash scripts, subshells (được viết trong cặp dấu ngoặc đơn) là 1 cách cách thuận tiện để nhóm các câu lệnh. Một ví dụ thông thường là tạm thời di chuyển vào một thư mục khác, ví dụ:
```bash
    # do something in current dir
    (cd /some/other/dir && other-command)
    # continue in original dir
```

- Trong Bash, có nhiều loại variable expansion. Kiểm tra sự tồn tại của 1 biến: `${name:?error message}`. Ví dụ, nếu script của bạn yêu cầu 1 tham số, chỉ cần viết `input_file=${1:?usage: $0 input_file`. Sử dụng giá trị mặc định nếu tham số không được truyền giá trị: `${name:-default}`. Nếu bạn muốn có thêm 1 tham số trong ví dụ trước, bạn có thể viết `output_file=${2:-logfile}`. Nếu `$2` bị bỏ qua, `output_file` sẽ được set là `logfile`. Biểu thức toán học: `i=$(( (i + 1) % 5 ))`. Dãy số: `{1..10}`. Trim string: `${var%suffix}` và `${var#prefix}`, ví dụ, nếu `var=foo.pdf`, thì `echo ${var%.pdf}.txt` sẽ là `foo.txt`.

- Khai triển dấu ngoặc nhọn `{`...`}` có thể giảm bớt việc gõ lại các từ trùng lặp và tự động nối các mục lại với nhau. Ví dụ, `mv foo.{txt,pdf} some-dir` sẽ di chuyển cả 2 file `foo.txt` và `foo.pdf`, `cp somefile{,.bak}` sẽ được khai triển thành `cp somefile somefile.bak` hoặc `mkdir -p test-{a,b,c}/subtest-{1,2,3}`.

- Output của một lệnh có thể được xem như 1 file thông qua `< (some command)`. Ví dụ, so sánh file `/etc/hosts` ở local và remote:
```sh
    diff /etc/hosts < (ssh somehost cat /etc/hosts)
```

- Khi viết scripts, bạn có thể đặt tất cả code trong cặp ngoặc nhọn. Nếu thiếu ký tự ngoặc đóng ngoặc, script của bạn sẽ không được chạy vì có lỗi cú pháp. Điều này có ích khi script của bạn có thể được download qua web, nó ngăn việc thực thi các script được download chưa hoàn chỉnh.
```bash
{
    # Your code here
}
```

- Biết về "here documents" trong Bash, `cat <<EOF ...`.

- Trong Bash, để chuyển hướng cả stdout và stderr, sử dụng: `some-command > logfile 2>&1` hoặc `some-command &> logfile`. Thông thường, để chắc chắn 1 command không nhận input từ terminal hoặc phụ thuộc vào terminal, bạn có thể chuyển hướng input vào `/dev/null`: `</dev/null`, điều này thường có ích khi bạn muốn chạy các tiến trình ngầm hoặc viết script tương tác qua SSH.

- Sử dụng `man ascii` để xem bảng ASCII. Để xem hướng dẫn về encoding, xem `man unicode`, `man utf-8` hoặc `man latin1`.

- Sử dụng `screen` hoặc [`tmux`](https://tmux.github.io/) để kết hợp (multiplex) các màn hình, đặc biệt có ích khi làm việc với ssh, thoát khỏi phiên làm việc hoặc kết nối lại phiên làm việc trước. `byobu` có thể cải tiến `screen` hoặc `tmux` để xem nhiều hơn thông tin và dễ dàng quản lý hơn. Một giải pháp thay thế nhỏ gọn dành cho việc giữ session hoạt động (session persistence) là [`dtach`](https://github.com/crigler/dtach).

- Biết về ssh port tunnel với tùy chọn `-L` hoặc `-D` (và thỉnh thoảng là `-R`), ví dụ, truy cập remote web site thông qua `localhost:9000`:
```sh
    ssh -L 9000:remote-host.com:80 user@example.com
```

- Một số tuỳ chỉnh ssh sau có thể có ích cho bạn, ví dụ, những cài đặt trong `~/.ssh/config` sau đây được dùng để tránh bị mất kết nối, nén dữ liệu (điều này có ích khi làm việc với scp để tiết kiệm bandwidth), và kết hợp (multiplex) các kênh đến cùng 1 server với bằng 1 file cấu hình ở máy local:
```
    TCPKeepAlive=yes
    ServerAliveInterval=15
    ServerAliveCountMax=6
    Compression=yes
    ControlMaster auto
    ControlPath /tmp/%r@%h:%p
    ControlPersist yes
```

- Một số tuỳ chọn khác liên quan đến ssh rất có thể gây ra các vấn đề về security và bạn nên sử dụng các tuỳ chọn đó một cách cẩn thận, vd: `StrictHostKeyChecking=no`, `ForwardAgent=yes`

- SSH có thể được thay thế bởi [`mosh`](https://mosh.mit.edu/).

- Để xem permissions của 1 file ở dạng số bát phân (vd: 775, 664,...):
```sh
    stat -c '%A %a %n' /etc/timezone
```

- Để tương tác trực tiếp với các giá trị từ output của command khác, sử dụng [`percol`](https://github.com/mooz/percol) hoặc [`fzf`](https://github.com/junegunn/fzf).

- Tương tác với tên file xuất hiện trong output của lệnh khác (vd: git), sử dụng `fpp` ([PathPicker](https://github.com/facebook/PathPicker)).

- Thiết lập 1 web server đơn giản cho tất cả file trong thư mục hiện tại (bao gồm cả các thư mục con), sử dụng:
Với Python 2: `python -m SimpleHTTPServer 7777` (port 7777)
Và Python 3:  `python -m http.server 7777`

- Để chạy 1 câu lệnh với tư cách là người khác, sử dụng `sudo`. Mặc định sẽ là user root, sử dụng tùy chọn `-u` để chỉ định 1 user khác hoặc `-i` để đăng nhập vào phiên làm việc của người đó (bạn sẽ được hỏi về mật khẩu _của bạn_).

- Để chuyển sang shell của user khác, sử dụng `su username` hoặc `su - username`. Ký tự nối "-" để tạo một môi trường như thể người đó đang login. User mặc định là root nếu không điền tham số username. Bạn sẽ được hỏi về  password _của user bạn đang chuyển sang_.

- Hiểu biết về [128K limit](https://wiki.debian.org/CommonErrorMessages/ArgumentListTooLong) về command lines. "Argument list too long" là lỗi thường xảy ra khi sử dụng wildcard để match số lượng lớn file (giải pháp thay thế là sử dụng `find` hoặc `xargs`).

- Sử dụng `python` như là 1 máy tính đơn giản:
VD:
```
>>> 2+3
5
```


## Processing files and data

- Để xác định vị trí 1 file bằng tên của file đó trong thư mục hiện tại: `find . -iname '*something*'`. Để tìm kiếm ở bất kỳ đâu trong máy tính, sử dụng `locate something` (tuy nhiên, hãy nhớ rằng những file vừa mới tạo có thể chưa được đánh chỉ mục, bạn cần phải chạy lệnh `updatedb`).

- Để tìm kiếm code từ nhiều file mã nguồn (chức năng nâng cao so với `grep -r`), sử dụng [`ag`](https://github.com/ggreer/the_silver_searcher).

- Để chuyển đổi HTML sang text: `lynx -dump -stdin`

- Để chuyển nhiều loại định dạng khác, như Markdown, HTML,... hãy thử [`pandoc`](http://pandoc.org/).

- Nếu bạn phải xử lý XML, sử dụng `xmlstarlet` dù đã cũ nhưng vẫn còn tốt.

- Sử dụng [`jq`](http://stedolan.github.io/jq/) để thao tác với JSON.

- Với YAML, sử dụng [`shyaml`](https://github.com/0k/shyaml).

- Với Excel hoặc CSV files, [csvkit](https://github.com/onyxfish/csvkit) cung cấp các command `in2csv`, `csvcut`, `csvjoin`, `csvgrep`,...

- Các công cụ với Amazon S3, [`s3cmd`](https://github.com/s3tools/s3cmd) và [`s4cmd`](https://github.com/bloomreach/s4cmd). Amazon's [`aws`](https://github.com/aws/aws-cli) và phiên bản cải thiện [`saws`](https://github.com/donnemartin/saws) là công cụ thiết yếu khi làm việc liên quan đến AWS.

- Biết sử dụng `sort` và `uniq`, `comm`, bao gồm các tùy chọn cho `uniq`: `-u` và `-d`, xem thêm về one-liners ở mục bên dưới.

- Sử dụng `cut`, `paste` và `join` để thao tác với text file. Nhiều người sử dụng `cut` nhưng không biết về `join`.

- Sử dụng `wc` để đếm số dòng (`-l`), số ký tự (`-m`), số từ (`-w`) và số bytes (`-c`).

- Sử dụng `tee` để vừa hiển thị output ra màn hình, vừa lưu vào file, vd: `ls -al | tee file.txt`.

- Đối với các tính toán phức tạp, thống kê trên dữ liệu, có thể sử dụng [`datamash`](https://www.gnu.org/software/datamash/).

- Locale của hệ thống ảnh hưởng nhiều đến các lệnh command line, bao gồm cách sắp xếp (collation) và hiệu suất. Phần lớn các phiên bản Linux sẽ đặt `LANG` hoặc các biến locale khác đều là US English. Nhưng lưu ý rằng thứ tự sắp xếp sẽ thay đổi nếu bạn thay đổi locale. Và các thủ tục i18n có thể làm cho việc sắp xếp hoặc các command khác chậm đi một cách đáng kể. Trong một số trường hợp (chẳng hạn các lệnh thiết lập hoặc các lệnh có tính nhất quán về output như bên dưới) bạn có thể bỏ qua các thủ tục i18n và sử dụng phương pháp sắp xếp cổ điển dựa theo byte bằng cách `export LC_ALL=C`.

- Bạn có thể thiết lập môi trường cụ thể cho mỗi lệnh bằng cách thêm vào trước lệnh đó một lệnh thiết lập môi trường, ví dụ: `TZ=Pacific/Fiji date`.

- Hiểu cơ bản về `awk` và `sed` cho các tác vụ [data munging](https://en.wikipedia.org/wiki/Data_wrangling). Ví dụ, tính tổng tất cả số trong cột thứ 3 của 1 file: `awk '{ x += $3 } END { print x }'`.

- Thay thế toàn bộ một string trong 1 hoặc nhiều file:
```sh
    perl -pi.bak -e 's/old-string/new-string/g' my-files-*.txt
```

- Để đổi tên nhiều file hoặc tìm kiếm và thay thế chuỗi trong file, sử dụng [`repren`](https://github.com/jlevy/repren). (Trong một số trường hợp `rename` command có thể đổi tên nhiều file, nhưng chú ý chức năng của nó có thể hoạt động không giống nhau trên tất cả các Linux distro).
```sh
    # Đổi tên file, thư mục và nội dung từ foo -> bar
    repren --full --preserve-case --from foo --to bar .
    # Đổi tên backup file whatever.bak -> whatever
    repren --renames --from '(.*)\.bak' --to '\1' *.bak
    # Sử dụng rename cho ví dụ trên:
    rename 's/\.bak$//' *.bak
```

- Theo thông tin trong man page, `rsync` thực sự là 1 công cụ copy file rất nhanh và linh hoạt. Nó được biết đến nhiều trong việc đồng bộ file giữa các máy, nhưng điều này cũng đúng khi đồng bộ các file ở local. Khi không bị hạn chế security, sử dụng `rsync` thay vì `scp` cho phép khôi phục lại quá trình di chuyển file mà không phải bắt đầu lại từ đầu. Nó cũng là một trong [những cách nhanh nhất để xóa 1 số lượng lớn các file](https://web.archive.org/web/20130929001850/http://linuxnote.net/jianingy/en/linux/a-fast-way-to-remove-huge-number-of-files.html).
```sh
mkdir empty && rsync -r --delete empty/ some-dir && rmdir some-dir
```

- `shuf` để trộn lẫn hoặc lựa chọn các dòng ngẫu nhiên từ 1 file.

- Các tùy chọn của `sort`. Với số, sử dụng `-n` hoặc `-h` để sắp xếp các số dạng human-readable (vd: kết quả từ hàm `du -h`). Hiểu cách hoạt động của `-t` và `-k`. Chú ý, bạn cần viết `-k1,1` để sắp xếp bởi một mình trường thứ nhất; `-k1` có nghĩa là sắp xếp theo cả dòng. Sắp xếp stable `sort -s` có thể hữu dụng, chẳng hạn, để sắp xếp lần thứ nhất bởi trường 2, sau đó sắp xếp theo trường 1, bạn có thể dùng `sort -k1,1 | sort -s -k2,2`.

- Nếu bạn từng phải viết viết 1 ký tự tab trong command line Bash (vd: tham số -t cho lệnh sort), bạn có thể dùng tổ hợp phím **ctrl-v** **[Tab]** hoặc viết `$'\t'` (cách này thường thuận tiện hơn vì bạn có thể copy/paste).

- Các công cụ chuẩn để patching source code là `diff` và `patch`. Xem thêm `diffstat` để xem tóm tắt của 1 file diff và `sdiff` để xem file diff theo dạng side-by-side. Ghi chú, `diff -r` áp dụng cho toàn bộ các thư mục. Sử dụng `diff -r tree1 tree2 | diffstat` để xem tóm tắt các thay đổi. Sử dụng `vimdiff` để so sánh và sửa file.

- Với các file binary, sử dụng `hd`, `hexdump` hoặc `xxd` xem ở dạng hex và `bvi`, `hexedit` để sửa.

- Cũng cho các file nhị phân, `strings` (cộng với `grep`,...) cho phép bạn tìm kiếm 1 đoạn text.

- Để diff các file nhị phân (delta compression), sử dụng `xdelta3`.

- Để chuyển đổi encoding, sử dụng `iconv`. Hoặc `uconv` để có nhiều tùy chọn nâng cao, nó hỗ trợ một số ký tự Unicode đặc biệt. Ví dụ: câu lệnh sau chuyển câu sang chữ thường và loại bỏ tất cả dấu nhấn trọng âm:
```sh
    uconv -f utf-8 -t utf-8 -x '::Any-Lower; ::Any-NFD; [:Nonspacing Mark:] >; ::Any-NFC; ' < input.txt > output.txt
```

- Để tách file thành nhiều phần, sử dụng `split` (tách theo kích thước) hoặc `csplit` (tách theo pattern).

- Để thao tác với các biểu thức liên quan đến ngày tháng, thời gian, sử dụng `dateadd`, `datediff` hoặc `strptime`,... từ [`dateutils`](http://www.fresse.org/dateutils/).

- Sử dụng `zless`, `zmore`, `zcat` và `zgrep` để thao tác với file nén.

- Các thuộc tính của file có thể được thiết lập bằng `chattr` và nó là một giải pháp cấp thấp hơn thay thế cho file permissions. Ví dụ, để bảo vệ file tránh bị xóa nhầm, sử dụng flag immutable: `sudo chattr +i /critical/directory/or/file`.

- Sử dụng `getfacl` và `setfacl` để lưu và phục hồi file permissions. Ví dụ:
```sh
   getfacl -R /some/path > permissions.txt
   setfacl --restore=permissions.txt
```

- Để tạo file trống, sử dụng `truncate` ([sparse file](https://en.wikipedia.org/wiki/Sparse_file)), `fallocate` (đối với các hệ thống ext4, xfs, btrfs và ocfs2), `xfs_mkfile` (hầu hết tất cả các loại hệ thống filesystems, từ package xfsprogs), `mkfile` (cho các hệ thống Unix-like như Solaris, Mac OS).

## System debugging

- Đối với debug web, `curl` và `curl -I` là khá tiện lợi, hoặc `wget`, [`httpie`](https://github.com/jkbrzt/httpie).

- Để xem trạng thái hiện tại của cpu, disk sử dụng `top` (hoặc `htop`), `iostat` và `iotop`. Sử dụng `iostat -mxz 15` để xem thông tin cơ bản về CPU, các phân vùng đĩa.

- Để xem chi tiết về kết nối mạng, sử dụng `netstat` và `ss`.

- Để xem nhanh tổng quan về điều gì đang xảy ra trên hệ thống, `dstat` đặc biệt có ích. Chi tiết hơn, sử dụng [`glances`](https://github.com/nicolargo/glances).

- Để xem trạng thái bộ nhớ, thử chạy và hiểu về output của lệnh `free` và `vmstat`. Thông thường, chú ý là giá trị "cached" là bộ nhớ được sử dụng bởi Linux kernel như 1 file cache, vì thế nó cũng được xem như là "free".

- Debug hệ thống Java rắc rối hơn một chút, nhưng với 1 mẹo nhỏ cho Oracle hoặc một số loại máy ảo JVM khác bạn có thể chạy `kill -3 <pid>` và stack trace, thông tin về bộ nhớ heap (bao gồm chi tiết về GC) sẽ được ghi vào stderr. Các lệnh của JDK `jps`, `jstat`, `jstack`, `jmap` cũng rất có ích. [SJK tools](https://github.com/aragozin/jvm-tools) dành cho các chức năng nâng cao hơn.

- [`mtr`](http://www.bitwizard.nl/mtr/) là 1 lựa chọn tốt hơn traceroute để xác định các vấn đề về mạng.

- Để xem lý do hết dung lượng ổ cứng, [`ncdu`](https://dev.yorhel.nl/ncdu) sẽ tiết kiệm cho bạn thời gian hơn so với lệnh thông thường `du -sh *`.

- Để tìm socket hoặc tiến trình nào đang sử dụng băng thông (bandwidth), sử dụng [`iftop`](http://www.ex-parrot.com/~pdw/iftop/) hoặc [`nethogs`](https://github.com/raboof/nethogs).

- Công cụ `ab` (từ Apache) dùng để kiểm tra nhanh về hiệu năng của web server. Chi tiết hơn, hãy thử `siege`.

- Các công khác để debug các vấn đề về mạng: [`wireshark`](https://wireshark.org/), [`tshark`](https://www.wireshark.org/docs/wsug_html_chunked/AppToolstshark.html), hoặc [`ngrep`](http://ngrep.sourceforge.net/).

- Hiểu về `strace` và `ltrace`. Những lệnh này rất có ích nếu  một chương trình bị lỗi, treo hoặc crash một cách bất thường hoặc bạn muốn xem một số thông tin chung chung về hiệu năng. Ghi chú về tùy chọn profiling `-c` và khả năng attach đến 1 tiến trình đang chạy. Sử dụng tùy chọn `-f` để theo vết cả những tiến trình con.

- `ldd` được dùng để kiểm tra shared libraries.

- Biết cách kết nối vào 1 tiến trình đang chạy với `gdb` và xem stack trace của nó.

- Sử dụng `/proc`. Thỉnh thoảng nó vô cùng tiện lợi để gỡ rối các vấn đề của các tiến trình đang chạy. Ví dụ: `/proc/cpuinfo`, `/proc/meminfo`, `/proc/cmdline`, `/proc/xxx/cwd`, `/proc/xxx/exe`, `/proc/xxx/fd/`, `/proc/xxx/smaps` (trong đó `xxx` là id của process hay pid).

- Khi điều tra các vấn đề trong quá khứ, [`sar`](http://sebastien.godard.pagesperso-orange.fr/) có thể có ích. Nó thống kê lịch sử trạng thái của CPU, memory, network,...

- Để phân tích sâu hơn về hệ thống và hiệu năng của hệ thống, hãy xem `stap` ([SystemTap](https://sourceware.org/systemtap/wiki)), [`perf`](https://en.wikipedia.org/wiki/Perf_%28Linux%29), và [`sysdig`](https://github.com/draios/sysdig).

- Kiểm tra thông tin hệ điều hành đang chạy: `uname` hoặc `uname -a` (thông tin về kernel) hoặc `lsb_release -a` (thông tin về Linux distro).

- Sử dụng `dmesg` khi có điều-gì-đó là lạ (có thể là các vấn đề về phần cứng hoặc driver).

- Nếu bạn xóa file nhưng nó không giải phóng bộ nhớ đĩa cứng theo kết quả của `df`, kiểm tra xem file đó có đang được sử dụng bởi tiến trình nào không: `lsof | grep deleted | grep "filename-of-my-big-file"`.


## One-liners

Một số ví dụ về việc kết hợp các lệnh:

- Đôi khi, việc bạn có thể tìm giao, hợp hoặc tìm sự khác nhau của các file text thông qua `sort`/`uniq` là rất hữu ích. Hai lệnh này chạy rất nhanh và có thể xử lý được các file rất lớn lên đến nhiều gigabytes (`sort` không bị giới bởi bộ nhớ, mặc dù bạn cần sử dụng tùy chọn `-T` nếu thư mục `/tmp` được đặt trên một phân vùng nhỏ). Xem thêm ghi chú về `LC_ALL` ở trên và tùy chọn `sort -u`.
```sh
    cat a b | sort | uniq > c   # c = a hợp b
    cat a b | sort | uniq -d > c   # c = a giao b
    cat a b b | sort | uniq -u > c   # c = a - b
```

- Sử dụng `grep . *` để xem xét nhanh nội dung của tất cả file trong thư mục (mỗi dòng trong output sẽ kèm theo tên file) hoặc `head -100 *` (hiển thị phần mở đầu của mỗi file). Điều này có ích khi làm việc với các thư mục bao gồm các file config như `/sys`, `/proc`, `/etc`.

- Tính tổng tất cả số trong cột thứ 3 của 1 file text (nhanh gấp khoảng 3 lần và code ít hơn 3 lần so với khi viết bằng Python):
```sh
    awk '{ x += $3 } END { print x }' myfile
```

- Để xem kích thước, ngày tháng của các file trong cây thư mục, tương tự như `ls -lR` nhưng có thể dễ đọc hơn:
```sh
    find . -type f -ls
```

- Giả sử bạn có 1 file text, chẳng hạn file log của web server và 1 giá trị nhất định xuất hiện trên một số dòng, ví dụ tham số `acct_id` của URL. Nếu bạn muốn kiểm tra có bao nhiêu request cho mỗi `acct_id`:
```sh
    cat access.log | egrep -o 'acct_id=[0-9]+' | cut -d= -f2 | sort | uniq -c | sort -rn
```

- Để theo dõi những thay đổi, sử dụng `watch`, ví dụ như theo dõi sự thay đổi của các file trong 1 thư mục với `watch -d -n 2 'ls -rtlh | tail'` hoặc theo dõi các thiết lập mạng trong lúc bạn đang xử lý sự cố về wifi với `watch -d -n 2 ifconfig`.

- Chạy hàm sau để xem một ghi chú ngẫu nhiên từ 1 tài liệu (phân tích Markdown và trích ra 1 mục):
```sh
    function taocl() {
        curl -s https://raw.githubusercontent.com/jlevy/the-art-of-command-line/master/README.md |
            pandoc -f markdown -t html |
            xmlstarlet fo --html --dropdtd |
            xmlstarlet sel -t -v "(html/body/ul/li[count(p)>0])[$RANDOM mod last()+1]" |
            xmlstarlet unesc | fmt -80
    }
```


## Obscure but useful

- `expr`: thực hiện các phép toán số học hoặc boolean hoặc biểu thức chính quy

- `m4`: bộ xử lý macro

- `yes`: in 1 chuỗi nhiều lần

- `cal`: calendar trực quan

- `env`: chạy 1 câu lệnh (có ích trong các Bash script)

- `printenv`: in ra các biến môi trường (có ích khi debug Bash script)

- `look`: tìm các từ tiếng Anh (hoặc các dòng trong 1 file) bắt đầu bằng 1 chuỗi nào đó

- `cut`, `paste` và `join`: xử lý dữ liệu text

- `fmt`: định dạng đoạn văn bản

- `pr`: định dạng văn bản thành các trang, cột

- `fold`: wrap text

- `column`: định dạng văn bản thành các cột hoặc bảng

- `expand` và `unexpand`: chuyển đổi giữa tab và space

- `nl`: đánh số dòng

- `seq`: in dãy số

- `bc`: máy tính số học

- `factor`: phân tích thừa số nguyên tố của 1 số

- [`gpg`](https://gnupg.org/): mã hóa và xác thực file

- `toe`: terminfo

- `nc`: network debugging and data transfer

- `socat`: socket relay and tcp port forwarder (similar to `netcat`)

- [`slurm`](https://github.com/mattthias/slurm): network traffic visualization

- `dd`: di chuyển dữ liệu giữa các file hoặc thiết bị

- `file`: xác định loại file

- `tree`: hiển thị cây thư mục

- `stat`: xem các thông tin của 1 file

- `time`: thực hiện và đo thời gian chạy 1 câu lệnh

- `timeout`: giới hạn thời gian thực thi 1 câu lệnh

- `lockfile`: tạo 1 file semaphore chỉ có thể xóa bởi `rm -f`

- `logrotate`: rotate, compress and mail logs.

- `watch`: chạy lặp lại 1 câu lệnh, hiển thị kết quả và các thay đổi

- `tac`: in đảo ngược nội dung của 1 file

- `shuf`: chọn ngẫu nhiên các dòng từ 1 file

- `comm`: so sánh file theo từng dòng

- `pv`: monitor the progress of data through a pipe

- `strings`: extract text from binary files

- `tr`: character translation or manipulation

- `iconv` or `uconv`: conversion for text encodings

- `split` and `csplit`: splitting files

- `sponge`: đọc tất cả input sau đó ghi, có ích khi đọc và ghi cùng 1 file, vd: `grep -v something some-file | sponge some-file`

- `units`: chuyển đổi đơn vị, xem thêm `/usr/share/units/definitions.units`

- `apg`: sing 1 mật khẩu ngẫu nhiên

- `xz`: high-ratio file compression

- `ldd`: dynamic library info

- `nm`: symbols from object files

- `ab`: benchmarking web servers

- `strace`: system call debugging

- [`mtr`](http://www.bitwizard.nl/mtr/): better traceroute for network debugging

- `cssh`: visual concurrent shell

- `rsync`: sync files and folders over SSH or in local file system

- [`wireshark`](https://wireshark.org/) and [`tshark`](https://www.wireshark.org/docs/wsug_html_chunked/AppToolstshark.html): packet capture and network debugging

- [`ngrep`](http://ngrep.sourceforge.net/): grep for the network layer

- `host` and `dig`: DNS lookups

- `lsof`: process file descriptor and socket info

- `dstat`: useful system stats

- [`glances`](https://github.com/nicolargo/glances): high level, multi-subsystem overview

- `iostat`: Disk usage stats

- `mpstat`: CPU usage stats

- `vmstat`: Memory usage stats

- `htop`: improved version of top

- `last`: login history

- `w`: who's logged on

- `id`: user/group identity info

- [`sar`](http://sebastien.godard.pagesperso-orange.fr/): historic system stats

- [`iftop`](http://www.ex-parrot.com/~pdw/iftop/) or [`nethogs`](https://github.com/raboof/nethogs): network utilization by socket or process

- `ss`: socket statistics

- `dmesg`: boot and system error messages

- `sysctl`: view and configure Linux kernel parameters at run time

- `hdparm`: SATA/ATA disk manipulation/performance

- `lsblk`: list block devices: a tree view of your disks and disk partitions

- `lshw`, `lscpu`, `lspci`, `lsusb`, `dmidecode`: hardware information, including CPU, BIOS, RAID, graphics, devices, etc.

- `lsmod` and `modinfo`: List and show details of kernel modules.

- `fortune`, `ddate`, and `sl`: um, well, it depends on whether you consider steam locomotives and Zippy quotations "useful"


## OS X only

Những nội dung này chỉ có tác dụng trên OSX

- Quản lý, cài đặt các package với `brew` (Homebrew) hoặc `port` (MacPorts).

- Sao chép output của bất kỳ lệnh nào vào 1 ứng dụng với `pbcopy` và `pbpaste`.

- Để sử dụng phím Option trên OSX Terminal như 1 phím Alt (ví dụ sử dụng các tổ hợp phím trong các phần trước **alt-b**, **alt-f**,...) mở Preferences -> Profiles -> Keyboard và chọn "Use Option as Meta key".

- Để mở 1 file bằng 1 ứng dụng desktop, sử dụng `open` hoặc `open -a /Applications/Whatever.app`.

- Spotlight: tìm kiếm file với `mdfind` và liệt kê metadata (như EXIF) với `mdls`.

- Chú ý rằng OSX được dựa trên BSD Unix, và rất nhiều câu lệnh (vd: `ps`, `ls`, `tail`, `awk`, `sed`) có rất nhiều khác biệt so với các lệnh Linux (chủ yếu từ System V Unix và GNU). Thường thì bạn có thể kiểm tra xem có sự khác biệt không bằng cách chú ý xem có dòng trong man page hay không "BSD General Commands Manual". Trong một số trường hợp các phiên bản GNU có thể được cài đặt (chẳng hạn `gawk` và `gsed` là phiên bản GNU của awk và sed). Nếu bạn viết Bash dành cho đa nền tảng, hãy tránh những lệnh đó (thay bằng Python hoặc `perl`) hoặc cần phải test kĩ hơn.

- Để xem thông tin phiên bản OSX, sử dụng `sw_vers`.

## Windows only

Những nội dung sau chỉ áp dụng cho Windows.

- Trên Windows 10, bạn có thể sử dụng [Bash on Ubuntu on Windows](https://msdn.microsoft.com/commandline/wsl/about), nó cung cấp một môi trường Bash với các tiện ích Unix command line. Nó cho phép chạy các chương trình Linux trên Windows, tuy nhiên nó không hỗ trợ chạy chương trình Windows từ Bash prompt.

- Một giải pháp khác để chạy các lệnh shell là cài đặt [Cygwin](https://cygwin.com/), đa phần các lệnh mô tả ở phần trước đều hoạt động trong môi trường Cygwin.

- Cài đặt bổ sung các chương trình Unix thông qua Cygwin's package manager.

- Sử dụng `mintty` cho cửa sổ dòng lệnh của bạn.

- Truy cập Windows clipboard thông qua `/dev/clipboard`.

- Chạy `cygstart` để mở file bằng ứng dụng mặc định.

- Truy cập Windows registry với `regtool`.

- Chú ý đường dẫn Windows `C:\` sẽ trở thành `/cygdrive/c` trong Cygwin và `/` trong Cygwin sẽ là `C:\cygwin` trong Windows. Chuyển đổi giữa Cygwin và Windows path với `cygpath`.

- Bạn có thể thực hiện phần lớn các việc quản trị Windows với command line bằng `wmic`.

- Một lựa chọn khác cho các công cụ Unix cho Windows là [Cash](https://github.com/dthree/cash), chỉ có một số ít lệnh được bao gồm.

- Thêm một lựa chọn cho các công cụ GNU trên Windows là [MinGW](http://www.mingw.org/) và package [MSYS](http://www.mingw.org/wiki/msys) để cung cấp các tiện ích như bash, gawk, make và grep.

## More resources

- [awesome-shell](https://github.com/alebcay/awesome-shell): A curated list of shell tools and resources.
- [awesome-osx-command-line](https://github.com/herrbischoff/awesome-osx-command-line): A more in-depth guide for the OS X command line.
- [Strict mode](http://redsymbol.net/articles/unofficial-bash-strict-mode/) for writing better shell scripts.
- [shellcheck](https://github.com/koalaman/shellcheck): A shell script static analysis tool. Essentially, lint for bash/sh/zsh.
- [Filenames and Pathnames in Shell](http://www.dwheeler.com/essays/filenames-in-shell.html): The sadly complex minutiae on how to handle filenames correctly in shell scripts.
- [Data Science at the Command Line](http://datascienceatthecommandline.com/#tools): More commands and tools helpful for doing data science, from the book of the same name

## Disclaimer

Với ngoại lệ là một số tác vụ nhỏ, code được viết ra để người khác có thể đọc được nó. Sức mạnh đi kèm với trách nhiệm. Thực tế bạn *có thể* làm một tác vụ trong Bash nhưng không có nghĩa là bạn nên làm như thế ;)


## License

[![Creative Commons License](https://i.creativecommons.org/l/by-sa/4.0/88x31.png)](http://creativecommons.org/licenses/by-sa/4.0/)

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/).
