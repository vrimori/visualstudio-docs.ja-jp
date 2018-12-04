---
title: 書式指定子 (C++)、デバッガーで |Microsoft Docs
ms.custom: ''
ms.date: 11/20/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- QuickWatch dialog box, format specifiers in C++
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- expressions [C++], format specifiers
- specifiers, watch variable format
- specifiers
- Watch window, format specifiers in C++
- watch variable symbols
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 0f6f3b7c-ce2c-4b4d-b14f-7589dbed5444
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 73cd5655a5cb843c29fb628a2ec233860410dc7c
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305742"
---
# <a name="format-specifiers-for-c-in-the-visual-studio-debugger"></a>Visual Studio デバッガーで C++ の書式指定子
値を表示する形式を変更することができます、**ウォッチ**書式指定子を使用してウィンドウ。  
  
 書式指定子を使用することもできます、**イミディ エイト**ウィンドウで、**コマンド**ウィンドウで、[トレース ポイント](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)、およびソース ウィンドウでもです。 これらのウィンドウで式を一時停止する場合に結果が、[データヒント](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)します。 [データヒント] の表示には、書式指定子が反映されます。  
  
> [!NOTE]
>  Visual Studio のネイティブ デバッガーが新しいデバッグ エンジンに変更されると、いくつかの新しい書式指定子が追加され、一部の古い構成が削除されました。 C++/CLI で相互運用 (ネイティブ コードとマネージド コードの混合) をデバッグする場合は、以前のデバッガーが引き続き使用されます。 
  
## <a name="set-format-specifiers"></a>セットの書式指定子  
次のコード例を使用します。  
  
```C++  
int main() {  
    int my_var1 = 0x0065;  
    int my_var2 = 0x0066;  
    int my_var3 = 0x0067;  
}  
```  
  
 追加、`my_var1`変数を**ウォッチ**デバッグ中にウィンドウ**デバッグ** > **Windows** > **を見る** > **ウォッチ 1**します。 次に、変数を右クリックし  **16 進数表示**します。 これで、**ウォッチ**値 0x0065 がウィンドウに表示されます。 整数ではなく文字としてこの値を表示するには、まずを右クリックし、選択を解除**16 進数表示**します。 文字の書式指定子を追加し、 **c**で、**名前**変数名の後の列。 **値**列が表示されます**101 'e'** します。  
  
 ![WatchFormatCPlus1](../debugger/media/watchformatcplus1.png "WatchFormatCPlus1")  
  
##  <a name="BKMK_Visual_Studio_2012_format_specifiers"></a> 書式指定子  
 次の表では、Visual Studio で使用できる書式指定子について説明します。 太字の指定子は、新しいデバッガーと C での相互運用機能デバッグではなくのみサポート/cli CLI。  
  
|指定子|形式|元の [ウォッチ] の値|表示される値|  
|---------------|------------|--------------------------|---------------------|  
|d|10 進整数|0x00000066|102|  
|o|符号なし 8 進整数。|0x00000066|000000000146|  
|x<br /><br /> **h**|16 進整数|102|0xcccccccc|  
|x<br /><br /> **H**|16 進整数|102|0xcccccccc|  
|c|単一文字|0x0065, c|101 'e'|  
|s|const char * 文字列 (引用符)|\<場所 >"hello world"|"hello world"|  
|**sb**|const char* 文字列 (引用符なし)|\<場所 >"hello world"|hello world|  
|s8|UTF-8 文字列|\<場所 >「これは、utf-8 のコーヒー カップ â˜•」|「これは、utf-8 のコーヒー カップ ☕」|
|**s8b**|UTF-8 文字列 (引用符なし)|\<場所 >"hello world"|hello world|  
|su|Unicode (utf-16 エンコーディング) 文字列 (引用符)|\<位置 > L"hello world"|L"hello world"<br /><br /> u"hello world"|  
|sub|Unicode (UTF-16 エンコード) 文字列 (引用符なし)|\<位置 > L"hello world"|hello world|  
|bstr|BSTR バイナリ文字列 (引用符)|\<位置 > L"hello world"|L"hello world"|  
|env|環境ブロック (2 つの null で終了する文字列)|\<位置 > L"=:: =::\\\\"|L"=:: =::\\\\\\0 = C: = C:\\\\windows\\\\system32\\0ALLUSERSPROFILE =…|
|**s32**|Utf-32 文字列 (引用符)|\<位置 > U"hello world"|u"hello world"|  
|**s32b**|UTF-32 文字列 (引用符なし)|\<位置 > U"hello world"|hello world|  
|**en**|enum|Saturday(6)|土曜日|  
|**hv**|ポインター型。検査されるポインター値が配列のヒープ割り当ての結果であることを意味します (たとえば、 `new int[3]`)。|\<位置>{\<最初のメンバー>}|\<位置 > {\<最初のメンバー >、 \<2 番目のメンバー >,…}|  
|**na**|オブジェクトのポインターのメモリ アドレスを非表示にします。|\<位置>, {member=value...}|{member=value...}|  
|**nd**|基底クラスの情報だけを表示し、派生クラスは無視します。|`(Shape*) square` には基底クラスおよび派生クラスの情報が含まれます。|基底クラスの情報だけを表示します。|  
|hr|HRESULT または Win32 エラー コード。 デバッガーは、それらを自動的にデコードすると、この指定子は Hresult の必要なくなりました。|S_OK|S_OK|  
|wc|Windows クラス フラグ|0x0010|WC_DEFAULTCHAR|  
|wm|Windows メッセージ番号|16|WM_CLOSE|  
|!|データ型の表示カスタマイズをすべて無視した、未処理の書式。|\<カスタマイズされた表現>|4|  
  
> [!NOTE]
>  ときに、 **hv**書式指定子が存在する、デバッガーはバッファーの長さを決定し、その要素数を表示しようとします。 デバッガーは配列の正確なバッファー サイズを常に判断できるとは限らないため、可能な場合には必ずサイズ指定子 `(pBuffer,[bufferSize])` を使用してください。 **Hv**書式指定子は、バッファー サイズがすぐに使用できる場合に便利です  
  
###  <a name="BKMK_Size_specifiers_for_pointers_as_arrays_in_Visual_Studio_2012"></a> 配列としてのポインターのサイズ指定子  
 オブジェクトに対するポインターを配列として表示する場合、整数または式で配列要素数を指定できます。 
  
|指定子|形式|元の [ウォッチ] の値|表示される値|  
|---------------|------------|---------------------------|---------------------|  
|n|10 進数または **16 進数** の整数|pBuffer,[32]<br /><br /> pBuffer,**[0x20]**|`pBuffer` を 32 要素の配列として表示します。|  
|**[exp]**|整数に評価される有効な C++ 式|pBuffer,[bufferSize]|pBuffer を `bufferSize` 要素の配列として表示します。|  
|**expand(n)**|整数に評価される有効な C++ 式|pBuffer, expand(2)|`pBuffer` の 3 番目の要素を表示します。|  
  
##  <a name="BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue"></a> C++/CLI での相互運用機能デバッグ用の書式指定子  
 **太字** で示されている指定子は、ネイティブおよび C++/CLI コードをデバッグする場合にのみサポートされます。  
  
|指定子|形式|元の [ウォッチ] の値|表示される値|  
|---------------|------------|--------------------------|---------------------|  
|**d**<br /><br />**i**|符号付き 10 進整数。|0xF000F065|-268373915|  
|**u**|符号なし 10 進整数。|0x0065|101|  
|o|符号なし 8 進整数。|0xF065|0170145|  
|x<br /><br />x|16 進整数|61541|0x0000f065|  
|**l**<br /><br />**h**|d、i、u、o、x、X の long 型または short 型のプレフィックス。|00406042|0x0c22|  
|**f**|符号付き浮動小数点数値。|(3./2.), f|1.500000|  
|**e**|符号付き指数表記。|(3.0/2.0)|1.500000e+000|  
|**g**|浮動小数点の符号付きまたは符号付きの科学的表記法<br/> いずれか短い方します。|(3.0/2.0)|1.5|  
|c|単一文字|\<location>|101 'e'|  
|s|const char *、(引用符) で|\<location>|"hello world"|  
|su|const wchar_t*<br /><br /> char16_t const\* (引用符) で|\<location>|L"hello world"|  
|sub|const wchar_t*<br /><br /> const char16_t\*|\<location>|hello world|  
|s8|const char *、(引用符) で|\<location>|"hello world"|  
|hr|HRESULT または Win32 エラー コード。<br/>デバッガーは、それらを自動的にデコードすると、この指定子は Hresult の必要なくなりました。|S_OK|S_OK|  
|wc|Windows クラス フラグ|0x00000040,|WC_DEFAULTCHAR|  
|wm|Windows メッセージ番号|0x0010|WM_CLOSE|  
|!|任意のデータ型のビューのカスタマイズを無視して、未処理の書式|\<カスタマイズされた表現>|4|  
  
###  <a name="BKMK_Format_specifiers_memory_locations_in_interop_debugging_and_C___edit_and_continue"></a> 書式指定子との相互運用機能デバッグでのメモリ位置の/cli CLI  
 次の表では、メモリ位置を使用する書式設定記号について説明します。 メモリ位置指定子は、任意の値、または位置を評価する式に使用できます。  
  
|シンボル|形式|元の [ウォッチ] の値|表示される値|  
|------------|------------|--------------------------|---------------------|  
|**ma**|64 ASCII 文字。|0x0012ffac|0x0012ffac .4...0...".0W&.......1W&.0.:W..1...."..1.JO&.1.2.."..1...0y....1|  
|**m**|16 バイトの 16 進数。16 文字の ASCII 文字が続きます。|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00 .4...0...".0W&amp;.|  
|**mb**|16 バイトの 16 進数。16 文字の ASCII 文字が続きます。|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00 .4...0...".0W&amp;.|  
|**mw**|8 ワード。|0x0012ffac|0x0012ffac 34B3 00CB 3084 8094 22FF 308A 2657 0000|  
|**md**|4 ダブルワード。|0x0012ffac|0x0012ffac 00CB34B3 80943084 308A22FF 00002657|  
|**mq**|2 クワドワード。|0x0012ffac|0x0012ffac 7ffdf00000000000 5f441a790012fdd4|  
|**mu**|2 バイト文字 (Unicode)|0x0012ffac|0x0012ffac 8478 77f4 ffff ffff 0000 0000 0000 0000|  
  
###  <a name="BKMK_Size_specifier_for_pointers_as_arrays_in_interop_debugging_and_C___edit_and_continue"></a> C++/CLI での相互運用機能デバッグでの配列としてのポインターのサイズ指定子  
 オブジェクトに対するポインターを配列として表示する場合、整数で配列要素数を指定できます。
  
|指定子|形式|正規表現|表示される値|  
|---------------|------------|----------------|---------------------|  
|n|10 進整数|pBuffer[32]|`pBuffer` を 32 要素の配列として表示します。|
