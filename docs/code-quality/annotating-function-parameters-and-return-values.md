---
title: "関数パラメーターおよび戻り値の注釈設定 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_Outptr_opt_result_bytebuffer_to_"
  - "_Inout_updates_all_opt_"
  - "_Post_equal_to_"
  - "_Outptr_opt_result_maybenull_"
  - "_Out_writes_bytes_all_"
  - "_Out_writes_all_opt_"
  - "_In_opt_"
  - "_Outptr_"
  - "_Outptr_result_maybenull_"
  - "_Outref_result_bytebuffer_all_maybenull_"
  - "_Inout_updates_opt_z_"
  - "_Inout_updates_z_"
  - "_Out_writes_"
  - "_Out_writes_to_ptr_opt_z_"
  - "_In_reads_to_ptr_opt_"
  - "_Ret_writes_to_maybenull_"
  - "_Outref_result_maybenull_"
  - "_Ret_writes_bytes_"
  - "_Outptr_result_bytebuffer_"
  - "_Out_writes_opt_"
  - "_Inout_updates_bytes_opt_"
  - "_In_z_"
  - "_Inout_updates_to_"
  - "_Ret_maybenull_"
  - "_Ret_writes_bytes_to_"
  - "_Ret_z_"
  - "_COM_Outptr_"
  - "_Ret_maybenull_z_"
  - "_Out_opt_"
  - "_In_reads_opt_z_"
  - "_Outptr_result_bytebuffer_to_"
  - "_Ret_notnull_"
  - "_COM_Outptr_opt_result_maybenull_"
  - "_Inout_updates_to_opt_"
  - "_Inout_updates_"
  - "_Outptr_opt_result_buffer_"
  - "_Outptr_result_buffer_to_"
  - "_Out_writes_to_ptr_opt_"
  - "_Out_writes_bytes_all_opt_"
  - "_Inout_updates_all_"
  - "_Deref_inout_range_"
  - "_Ret_writes_"
  - "_Out_writes_z_"
  - "_Ret_writes_to_"
  - "_Out_writes_to_ptr_z_"
  - "_Out_writes_bytes_to_opt_"
  - "_In_reads_or_z_"
  - "_Inout_updates_bytes_to_"
  - "_In_reads_z_"
  - "_In_opt_z_"
  - "_Outref_result_buffer_maybenull_"
  - "_Ret_range_"
  - "_COM_Outptr_opt_"
  - "_Ouptr_opt_result_maybenull_z_"
  - "_In_reads_opt_"
  - "_Inout_"
  - "_Field_range_"
  - "_Ret_writes_z_"
  - "_Out_writes_to_"
  - "_Out_writes_to_ptr_"
  - "_Inout_opt_z_"
  - "_Outref_"
  - "_Deref_out_range_"
  - "_Outref_result_buffer_"
  - "_Outref_result_buffer_to_"
  - "_Outref_result_bytebuffer_to_maybenull_"
  - "_In_reads_bytes_"
  - "_Outptr_opt_result_buffer_to_"
  - "_Outref_result_buffer_all_"
  - "_Out_writes_bytes_to_"
  - "_Result_zeroonfailure_"
  - "_In_reads_bytes_opt_"
  - "_Outref_result_buffer_to_maybenull_"
  - "_Outref_result_bytebuffer_all_"
  - "_Outref_result_buffer_all_maybenull_"
  - "_Ret_writes_maybenull_z_"
  - "_In_range_"
  - "_Inout_updates_bytes_all_opt_"
  - "_Outref_result_bytebuffer_to_"
  - "_Inout_updates_bytes_to_opt_"
  - "_Pre_equal_to_"
  - "_Ret_writes_bytes_maybenull_"
  - "_COM_Outptr_result_maybenull_"
  - "_Ret_writes_maybenull_"
  - "_Out_writes_bytes_"
  - "_Outptr_opt_"
  - "_Out_writes_opt_z_"
  - "_Outref_result_nullonfailure_"
  - "_Outptr_opt_result_z_"
  - "_Inout_opt_"
  - "_Deref_in_range_"
  - "_Outptr_result_z_"
  - "_In_reads_to_ptr_opt_z_"
  - "_Struct_size_bytes_"
  - "_Outptr_result_nullonfailure_"
  - "_In_"
  - "_Inout_updates_bytes_"
  - "_In_reads_to_ptr_z_"
  - "_Ret_writes_bytes_to_maybenull"
  - "_Outptr_opt_result_nullonfailure_"
  - "_In_reads_to_ptr_"
  - "_Outptr_result_buffer_"
  - "_Out_"
  - "_Outref_result_bytebuffer_maybenull_"
  - "_Outptr_result_maybenull_z_"
  - "_In_reads_"
  - "_Inout_updates_opt_"
  - "_Out_writes_to_opt_"
  - "_Outptr_opt_result_bytebuffer_"
  - "_Out_writes_all_"
  - "_Out_range_"
  - "_Inout_updates_bytes_all_"
  - "_Inout_z_"
  - "_Outref_result_bytebuffer_"
  - "_Result_nullonfailure_"
  - "_Ret_null_"
ms.assetid: 82826a3d-0c81-421c-8ffe-4072555dca3a
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 関数パラメーターおよび戻り値の注釈設定
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

単純な関数のパラメーターには、注釈の典型的な使用方法を説明: スカラー、および構造体とクラスへのポインター- およびほとんどの種類のバッファー。  注釈の一般的な使用パターンについても説明します。 関数に関連付けられている注釈を追加している、次を参照してください [関数の動作に注釈を付ける。](../code-quality/annotating-function-behavior.md)  
  
## <a name="pointer-parameters"></a>ポインター パラメーター  
 次の表に注釈、ポインター パラメーターの注釈が付けられたが、ときに、アナライザー エラーを報告、ポインターが null の場合。  これには、ポインターとが指すデータ項目が適用されます。  
  
 **注釈と説明**  
  
-   `_In_`  
  
     スカラー、構造体、構造体へのポインターなどの入力パラメーターに注釈を付けます。  明示的に上で使用できます単純なスカラーです。  パラメーターは、前の状態で有効にする必要がありは変更されません。  
  
-   `_Out_`  
  
     スカラー、構造体、構造体へのポインターのような出力パラメーターに注釈を付けます。  この値を返すことをオブジェクトに当てはまらない — たとえば、スカラー値によって渡される。  パラメーターが有効である前の状態にする必要はありませんが、後の状態で有効にする必要があります。  
  
-   `_Inout_`  
  
     関数によって変更されるパラメーターに注釈を付けます。  前の状態と後の状態の両方で有効にする必要がありますが、呼び出しの前後に異なる値を持つと見なされます。 変更可能な値に適用する必要があります。  
  
-   `_In_z_`  
  
     入力として使用される null で終わる文字列へのポインター。  文字列は、前の状態で有効である必要があります。  バリアント `PSTR`, 、既に正しい注釈を付けるは優先的に使用します。  
  
-   `_Inout_z_`  
  
     変更は、null で終わる文字配列へのポインター。  前に、と呼び出しの後は、有効にする必要がありますが、値が変更されていると見なされます。  Null 終端文字が移動されてが、元の null 終端文字までの要素のみがアクセス可能です。  
  
-   `_In_reads_(s)`  
  
     `_In_reads_bytes_(s)`  
  
     関数によって読み込まれます配列へのポインター。  配列のサイズは `s` 要素、これらはすべて有効にする必要があります。  
  
      `_bytes_` バリアントが要素ではなくバイト単位でサイズを提供します。 サイズは、要素として表現できない場合にのみに使用します。  たとえば、 `char` 文字列を使用、 `_bytes_` バリアントの場合は、類似した機能を使用する `wchar_t` とします。  
  
-   `_In_reads_z_(s)`  
  
     Null で終わるを既知のサイズを持つ配列へのポインター。 Null 終端文字までの要素: または `s` null 終端文字がない場合、前の状態で有効にする必要があります。  バイト単位でサイズがわかっている場合は、スケール `s` で要素のサイズ。  
  
-   `_In_reads_or_z_(s)`  
  
     Null で終わるか、既知のサイズまたはその両方を配列へのポインター。 Null 終端文字までの要素: または `s` null 終端文字がない場合、前の状態で有効にする必要があります。  バイト単位でサイズがわかっている場合は、スケール `s` で要素のサイズ。  (ため、 `strn` ファミリです)。  
  
-   `_Out_writes_(s)`  
  
     `_Out_writes_bytes_(s)`  
  
     配列へのポインター `s` 要素 (上がって バイト単位)、関数によって書き込まれます。  配列の要素は、有効な状態にある前、する必要はありませんし、後の状態の有効な要素の数は指定されていません。  パラメーターの型の注釈がある場合は、後の状態に適用されます。 次に例を示します。  
  
     `typedef _Null_terminated_ wchar_t *PWSTR; void MyStringCopy(_Out_writes_ (size) PWSTR p1,    _In_ size_t size,    _In_ PWSTR p2);`  
  
     この例では、呼び出し元がのバッファーを提供 `size` 要素 `p1`します。  `MyStringCopy` 有効なにより、それらの要素の一部です。 さらに、 `_Null_terminated_` 注釈で `PWSTR` ことを意味 `p1` 後の状態では null で終わります。  この方法では、有効な要素の数がまだ正しく定義されてが特定の要素の数は必要ありません。  
  
      `_bytes_` バリアントが要素ではなくバイト単位でサイズを提供します。 サイズは、要素として表現できない場合にのみに使用します。  たとえば、 `char` 文字列を使用、 `_bytes_` バリアントの場合は、類似した機能を使用する `wchar_t` とします。  
  
-   `_Out_writes_z_(s)`  
  
     配列へのポインター `s` 要素。  要素を前の状態で有効である必要はありません。  を通じて、null 終端の要素を後の状態に、存在する必要があります: 有効にする必要があります。  バイト単位でサイズがわかっている場合は、スケール `s` で要素のサイズ。  
  
-   `_Inout_updates_(s)`  
  
     `_Inout_updates_bytes_(s)`  
  
     両方の読み取りし、書き込みに関数が配列へのポインター。  サイズの `s` 要素であり、前の状態および状態の後に有効です。  
  
      `_bytes_` バリアントが要素ではなくバイト単位でサイズを提供します。 サイズは、要素として表現できない場合にのみに使用します。  たとえば、 `char` 文字列を使用、 `_bytes_` バリアントの場合は、類似した機能を使用する `wchar_t` とします。  
  
-   `_Inout_updates_z_(s)`  
  
     Null で終わるを既知のサイズを持つ配列へのポインター。 Null の終端からの要素を — 存在する必要があります: 前の状態と後の状態の両方で有効にする必要があります。  後の状態の値は、前の状態の値と異なると見なされますこれには、null 終端文字の場所が含まれます。 バイト単位でサイズがわかっている場合は、スケール `s` で要素のサイズ。  
  
-   `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     配列へのポインター `s` 要素。  要素を前の状態で有効である必要はありません。  までの要素の後の状態で、 `c`番目の要素を有効にする必要があります。  バイト単位でサイズがわかっている場合は、スケール `s` と `c` 要素のサイズまたは使用する、 `_bytes_` バリアントでは、定義されています。  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     つまり、すべての要素まで、バッファー内に存在する `s` 前の状態が有効で、後の状態にします。  例:  
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
-   `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     配列が読み取りおよび書き込み関数へのポインター。  サイズの `s` 要素、これらはすべて有効な状態でなければなりません前、および `c` 要素は後の状態で有効である必要があります。  
  
      `_bytes_` バリアントが要素ではなくバイト単位でサイズを提供します。 サイズは、要素として表現できない場合にのみに使用します。  たとえば、 `char` 文字列を使用、 `_bytes_` バリアントの場合は、類似した機能を使用する `wchar_t` とします。  
  
-   `_Inout_updates_z_(s)`  
  
     Null で終わるを既知のサイズを持つ配列へのポインター。 Null の終端からの要素を — 存在する必要があります: 前の状態と後の状態の両方で有効にする必要があります。  後の状態の値は、前の状態の値と異なると見なされますこれには、null 終端文字の場所が含まれます。 バイト単位でサイズがわかっている場合は、スケール `s` で要素のサイズ。  
  
-   `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     配列へのポインター `s` 要素。  要素を前の状態で有効である必要はありません。  までの要素の後の状態で、 `c`番目の要素を有効にする必要があります。  バイト単位でサイズがわかっている場合は、スケール `s` と `c` 要素のサイズまたは使用する、 `_bytes_` バリアントでは、定義されています。  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     つまり、すべての要素まで、バッファー内に存在する `s` 前の状態が有効で、後の状態にします。  例:  
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
-   `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     配列が読み取りおよび書き込み関数へのポインター。  サイズの `s` 要素、これらはすべて有効な状態でなければなりません前、および `c` 要素は後の状態で有効である必要があります。  
  
      `_bytes_` バリアントが要素ではなくバイト単位でサイズを提供します。 サイズは、要素として表現できない場合にのみに使用します。  たとえば、 `char` 文字列を使用、 `_bytes_` バリアントの場合は、類似した機能を使用する `wchar_t` とします。  
  
-   `_Inout_updates_all_(s)`  
  
     `_Inout_updates_bytes_all_(s)`  
  
     これは、読み取りおよび書き込みサイズの関数によって、配列へのポインター `s` 要素。 同等として定義されています。  
  
     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`  
  
     つまり、すべての要素まで、バッファー内に存在する `s` 前の状態が有効で、前の状態と後の状態にします。  
  
      `_bytes_` バリアントが要素ではなくバイト単位でサイズを提供します。 サイズは、要素として表現できない場合にのみに使用します。  たとえば、 `char` 文字列を使用、 `_bytes_` バリアントの場合は、類似した機能を使用する `wchar_t` とします。  
  
-   `_In_reads_to_ptr_(p)`  
  
     配列へのポインター式 `p` – `_Curr_` (つまり、 `p` マイナス `_Curr_`) 適切な言語の標準によって定義されます。  前のバージョン要素 `p` 前の状態で有効にする必要があります。  
  
-   `_In_reads_to_ptr_z_(p)`  
  
     Null で終わる配列へのポインター式 `p` – `_Curr_` (つまり、 `p` マイナス `_Curr_`) 適切な言語の標準によって定義されます。  前のバージョン要素 `p` 前の状態で有効にする必要があります。  
  
-   `_Out_writes_to_ptr_(p)`  
  
     配列へのポインター式 `p` – `_Curr_` (つまり、 `p` マイナス `_Curr_`) 適切な言語の標準によって定義されます。  前のバージョン要素 `p` する前の状態で有効である必要はありませんし、後の状態で有効にする必要があります。  
  
-   `_Out_writes_to_ptr_z_(p)`  
  
     Null で終わる配列へのポインター式 `p` – `_Curr_` (つまり、 `p` マイナス `_Curr_`) 適切な言語の標準によって定義されます。  前のバージョン要素 `p` する前の状態で有効である必要はありませんし、後の状態で有効にする必要があります。  
  
## <a name="optional-pointer-parameters"></a>省略可能なポインター パラメーター  
 ポインター パラメーターの注釈が含まれています `_opt_`, 、パラメーターを null にすることがあることを示します。 それ以外の場合、含まれていないものと同じ実行注釈 `_opt_`します。 次の一覧を `_opt_` ポインター パラメーターの注釈のバリエーション。  
  
||||  
|-|-|-|  
|`_In_opt_`<br /><br /> `_Out_opt_`<br /><br /> `_Inout_opt_`<br /><br /> `_In_opt_z_`<br /><br /> `_Inout_opt_z_`<br /><br /> `_In_reads_opt_`<br /><br /> `_In_reads_bytes_opt_`<br /><br /> `_In_reads_opt_z_`|`_Out_writes_opt_`<br /><br /> `_Out_writes_opt_z_`<br /><br /> `_Inout_updates_opt_`<br /><br /> `_Inout_updates_bytes_opt_`<br /><br /> `_Inout_updates_opt_z_`<br /><br /> `_Out_writes_to_opt_`<br /><br /> `_Out_writes_bytes_to_opt_`<br /><br /> `_Out_writes_all_opt_`<br /><br /> `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`<br /><br /> `_Inout_updates_bytes_to_opt_`<br /><br /> `_Inout_updates_all_opt_`<br /><br /> `_Inout_updates_bytes_all_opt_`<br /><br /> `_In_reads_to_ptr_opt_`<br /><br /> `_In_reads_to_ptr_opt_z_`<br /><br /> `_Out_writes_to_ptr_opt_`<br /><br /> `_Out_writes_to_ptr_opt_z_`|  
  
## <a name="output-pointer-parameters"></a>出力のポインター パラメーター  
 ポインターの出力パラメーターでは、null させずに、パラメーターで示される場所を区別するために特殊な表記法が必要です。  
  
 **注釈と説明**  
  
-   `_Outptr_`  
  
     パラメーターを null にすることはできませんし、後の状態で示される場所が null にすることはできませんし、有効にする必要があります。  
  
-   `_Outptr_opt_`  
  
     パラメーターが null であるが、後の状態で示される場所が null にすることはできませんし、有効にする必要があります。  
  
-   `_Outptr_result_maybenull_`  
  
     パラメーターを null にすることはできませんし、後の状態では、示される場所を null にすることができます。  
  
-   `_Outptr_opt_result_maybenull_`  
  
     パラメーターが null であるし、後の状態では、示される場所を null にすることができます。  
  
 次の表に、その他の部分文字列は、注釈の意味をさらに限定する注釈名に挿入されます。  さまざまな部分文字列は `_z`, 、`_COM_`, 、`_buffer_`, 、`_bytebuffer_`, 、および `_to_`です。  
  
> [!IMPORTANT]
>  注釈は、インターフェイスが COM の場合は、これらの注釈の COM フォームを使用します。 その他の種類のインターフェイスでは、COM 注釈を使用しないでください。  
  
 **注釈と説明**  
  
-   `_Outptr_result_z_`  
  
     `_Outptr_opt_result_z_`  
  
     `_Outptr_result_maybenull_z_`  
  
     `_Ouptr_opt_result_maybenull_z_`  
  
     返されたポインターが、 `_Null_terminated_` 注釈。  
  
-   `_COM_Outptr_`  
  
     `_COM_Outptr_opt_`  
  
     `_COM_Outptr_result_maybenull_`  
  
     `_COM_Outptr_opt_result_maybenull_`  
  
     返されたポインター COM のセマンティクスがあり、したがってを伝送、 `_On_failure_` 事後条件の戻り値のポインターが null であることです。  
  
-   `_Outptr_result_buffer_(s)`  
  
     `_Outptr_result_bytebuffer_(s)`  
  
     `_Outptr_opt_result_buffer_(s)`  
  
     `_Outptr_opt_result_bytebuffer_(s)`  
  
     返されたポインターが有効なサイズのバッファーを指す `s` 要素またはバイト数。  
  
-   `_Outptr_result_buffer_to_(s, c)`  
  
     `_Outptr_result_bytebuffer_to_(s, c)`  
  
     `_Outptr_opt_result_buffer_to_(s,c)`  
  
     `_Outptr_opt_result_bytebuffer_to_(s,c)`  
  
     返されたポインターがサイズのバッファーを指す `s` 要素またはバイト数のうち、最初の `c` 有効です。  
  
 インターフェイスの所定の規則は、失敗した場合の出力パラメーターを nullified することを推測します。  明示的に COM コードなどを除くは、次の表に、そのフォームが優先します。  COM コードの場合は、前のセクションで示されている、対応する COM 形式を使用します。  
  
 **注釈と説明**  
  
-   `_Result_nullonfailure_`  
  
     その他の注釈を変更します。 結果は、関数が失敗した場合は null に設定されます。  
  
-   `_Result_zeroonfailure_`  
  
     その他の注釈を変更します。 関数が失敗した場合、結果は 0 に設定します。  
  
-   `_Outptr_result_nullonfailure_`  
  
     返されたポインターは、関数が失敗した場合、関数が成功した場合、有効なバッファーまたは null を指します。 この注釈はオプションではないパラメーターです。  
  
-   `_Outptr_opt_result_nullonfailure_`  
  
     返されたポインターは、関数が失敗した場合、関数が成功した場合、有効なバッファーまたは null を指します。 この注釈は省略可能なパラメーターです。  
  
-   `_Outref_result_nullonfailure_`  
  
     返されたポインターは、関数が失敗した場合、関数が成功した場合、有効なバッファーまたは null を指します。 この注釈は参照パラメーターです。  
  
## <a name="output-reference-parameters"></a>出力の参照パラメーター  
 参照パラメーターの一般的な用途は、出力パラメーターです。  単純な出力の参照パラメーターの — たとえば、 `int&`—`_Out_` 正しいセマンティクスを提供します。  ただし、出力値がポインター — たとえば `int *&`— 同等ポインター注釈と同様に `_Outptr_ int **` 正しいセマンティクスを提供しません。  ポインター型の出力の参照パラメーターのセマンティクスを簡潔に記述するには、このような複合注釈を使用します。  
  
 **注釈と説明**  
  
-   `_Outref_`  
  
     結果は、後の状態で有効にする必要があり、null にすることはできません。  
  
-   `_Outref_result_maybenull_`  
  
     結果は、後の状態で有効にする必要がありますが、後の状態に null にすることがあります。  
  
-   `_Outref_result_buffer_(s)`  
  
     結果は、後の状態で有効にする必要があり、null にすることはできません。 サイズの有効なバッファーを指す `s` 要素。  
  
-   `_Outref_result_bytebuffer_(s)`  
  
     結果は、後の状態で有効にする必要があり、null にすることはできません。 サイズの有効なバッファーを指す `s` バイトです。  
  
-   `_Outref_result_buffer_to_(s, c)`  
  
     結果は、後の状態で有効にする必要があり、null にすることはできません。 バッファーを指す `s` 要素のうち、最初の `c` 有効です。  
  
-   `_Outref_result_bytebuffer_to_(s, c)`  
  
     結果は、後の状態で有効にする必要があり、null にすることはできません。 バッファーを指す `s` うちバイト最初 `c` が有効です。  
  
-   `_Outref_result_buffer_all_(s)`  
  
     結果は、後の状態で有効にする必要があり、null にすることはできません。 サイズの有効なバッファーを指す `s` 有効な要素です。  
  
-   `_Outref_result_bytebuffer_all_(s)`  
  
     結果は、後の状態で有効にする必要があり、null にすることはできません。 有効なバッファーを指す `s` 有効な要素のバイト数。  
  
-   `_Outref_result_buffer_maybenull_(s)`  
  
     結果は、後の状態で有効にする必要がありますが、後の状態に null にすることがあります。 サイズの有効なバッファーを指す `s` 要素。  
  
-   `_Outref_result_bytebuffer_maybenull_(s)`  
  
     結果は、後の状態で有効にする必要がありますが、後の状態に null にすることがあります。 サイズの有効なバッファーを指す `s` バイトです。  
  
-   `_Outref_result_buffer_to_maybenull_(s, c)`  
  
     結果は、後の状態で有効にする必要がありますが、後の状態に null にすることがあります。 バッファーを指す `s` 要素のうち、最初の `c` 有効です。  
  
-   `_Outref_result_bytebuffer_to_maybenull_(s,c)`  
  
     結果は、後の状態で有効にする必要がありますが、後の状態で null にすることがあります。 バッファーを指す `s` うちバイト最初 `c` が有効です。  
  
-   `_Outref_result_buffer_all_maybenull_(s)`  
  
     結果は、後の状態で有効にする必要がありますが、後の状態で null にすることがあります。 サイズの有効なバッファーを指す `s` 有効な要素です。  
  
-   `_Outref_result_bytebuffer_all_maybenull_(s)`  
  
     結果は、後の状態で有効にする必要がありますが、後の状態で null にすることがあります。 有効なバッファーを指す `s` 有効な要素のバイト数。  
  
## <a name="return-values"></a>戻り値  
 関数の戻り値のような `_Out_` パラメーター de-reference のさまざまなレベルでは、結果へのポインターの概念を考慮する必要はありません。  次の注釈では、戻り値は注釈付きのオブジェクト、スカラー、構造体へのポインターまたはバッファーへのポインター。 これらの注釈は、対応する同じセマンティクスを持つ `_Out_` 注釈。  
  
|||  
|-|-|  
|`_Ret_z_`<br /><br /> `_Ret_writes_(s)`<br /><br /> `_Ret_writes_bytes_(s)`<br /><br /> `_Ret_writes_z_(s)`<br /><br /> `_Ret_writes_to_(s,c)`<br /><br /> `_Ret_writes_maybenull_(s)`<br /><br /> `_Ret_writes_to_maybenull_(s)`<br /><br /> `_Ret_writes_maybenull_z_(s)`|`_Ret_maybenull_`<br /><br /> `_Ret_maybenull_z_`<br /><br /> `_Ret_null_`<br /><br /> `_Ret_notnull_`<br /><br /> `_Ret_writes_bytes_to_`<br /><br /> `_Ret_writes_bytes_maybenull_`<br /><br /> `_Ret_writes_bytes_to_maybenull_`|  
  
## <a name="other-common-annotations"></a>その他の一般的な注釈  
 **注釈と説明**  
  
-   `_In_range_(low, hi)`  
  
     `_Out_range_(low, hi)`  
  
     `_Ret_range_(low, hi)`  
  
     `_Deref_in_range_(low, hi)`  
  
     `_Deref_out_range_(low, hi)`  
  
     `_Deref_inout_range_(low, hi)`  
  
     `_Field_range_(low, hi)`  
  
     パラメーター、フィールド、または結果が範囲 (包括) から `low` に `hi`します。  等価 `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)` 済み状態または状態後の適切な条件と共に注釈付きのオブジェクトに適用されています。  
  
    > [!IMPORTANT]
    >  名前は、"in"と"out"のセマンティクスを含める `_In_` と `_Out_` は **いない** これらの注釈に適用します。  
  
-   `_Pre_equal_to_(expr)`  
  
     `_Post_equal_to_(expr)`  
  
     注釈付きの値が正確に `expr`します。  等価 `_Satisfies_(_Curr_ == expr)` 済み状態または状態後の適切な条件と共に注釈付きのオブジェクトに適用されています。  
  
-   `_Struct_size_bytes_(size)`  
  
     構造体またはクラス宣言に適用されます。  指定されているバイト数とその型の有効なオブジェクトを宣言された型よりも大きいする可能性があることを示します `size`します。  例:  
  
     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`  
  
     パラメーターのバイト単位のバッファー サイズ `pM` 型の `MyStruct *` に行われます。  
  
     `min(pM->nSize, sizeof(MyStruct))`  
  
## <a name="related-resources"></a>関連資料  
 [コード分析チームのブログ](http://go.microsoft.com/fwlink/?LinkId=251197)  
  
## <a name="see-also"></a>関連項目  
 [SAL 注釈を使用した C と C++ コード障害を減らす](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [SAL について](../code-quality/understanding-sal.md)   
 [関数の動作に注釈を付ける](../code-quality/annotating-function-behavior.md)   
 [構造体とクラスに注釈を付ける](../code-quality/annotating-structs-and-classes.md)   
 [ロック動作に注釈を付ける](../code-quality/annotating-locking-behavior.md)   
 [注釈を適用するタイミングと場所を指定します。](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [組み込み関数](../code-quality/intrinsic-functions.md)   
 [ベスト プラクティスと例](../code-quality/best-practices-and-examples-sal.md)