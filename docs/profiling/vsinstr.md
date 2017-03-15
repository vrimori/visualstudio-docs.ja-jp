---
title: "VSInstr | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "パフォーマンス ツール、インストルメンテーション"
  - "インストルメンテーション、VSInstr ツール"
  - "プロファイル ツール、VSInstr ツール"
  - "パフォーマンス ツール、インストルメンテーション"
  - "コマンド ライン、ツール"
  - "VSInstr"
  - "VSInstr ツール"
  - "パフォーマンス ツール、VSInstr ツール"
ms.assetid: 7b1334f7-f9b0-4a82-a145-d0607bfa8467
caps.latest.revision: 44
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 44
---
# VSInstr
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSInstr ツールは、バイナリをインストルメントするために使用します。  VSInstr ツールを起動するには、次の構文を使用します。  
  
```  
VSInstr [/U] filename [/options]  
```  
  
 VSInstr ツールのオプションの説明を次の表に示します。  
  
|オプション|説明|  
|-----------|--------|  
|**Help** または **?**|ヘルプを表示します。|  
|**U**|リダイレクトされたコンソール出力を Unicode で書き込みます。  最初に指定する必要があります。|  
|`@filename`|1 行につき 1 つのコマンド オプションを含む応答ファイルの名前を指定します。引用符は使用しないでください。|  
|**OutputPath** `:path`|インストルメントされたイメージの保存先ディレクトリを指定します。  出力パスを指定しなかった場合、元のバイナリは同じディレクトリ内で "Orig"という文字列を付け加えた名前に変更されます。インストルメンテーションには、バイナリのコピーが使用されます。|  
|**Exclude** `:funcspec`|プローブによるインストルメンテーションから除外する機能仕様を指定します。  このオプションは、関数へのプロファイリング プローブの挿入によって予測不可能な結果や好ましくない結果が引き起こされる場合に便利です。<br /><br /> 同じバイナリ内の関数を参照する **Exclude** オプションと **Include** オプションは使用しないでください。<br /><br /> 別個の **Exclude** オプションを使用して複数の機能仕様を指定できます。<br /><br /> `funcspec` は次のように定義します。<br /><br /> namespaceseparator1\<\>\[\] \[\] classseparator2\<\>関数<br /><br /> \<separator1 は\> ネイティブ コードの `::`、およびマネージ コードの `.` です。<br /><br /> \<separator2 `::`\> は常になります。<br /><br /> **Exclude** は、コード カバレッジでサポートされます。<br /><br /> ワイルドカード文字 \* がサポートされています。  たとえば、名前空間のすべての関数を除外するには、次を使用します。<br /><br /> MyNamespace::\*<br /><br /> **VSInstr \/DumpFuncs** を使用して、指定したバイナリの関数の完全な名前を一覧表示できます。|  
|**Include** `:funcspec`|プローブと共にインストルメントするバイナリ内の機能仕様を指定します。  バイナリ内のその他の関数はインストルメントされません。<br /><br /> 別個の **Include** オプションを使用して複数の機能仕様を指定できます。<br /><br /> 同じバイナリ内の関数を参照する **Include** オプションと **Exclude** オプションは使用しないでください。<br /><br /> **Include** は、コード カバレッジでサポートされません。<br /><br /> `funcspec` は次のように定義します。<br /><br /> namespaceseparator1\<\>\[\] \[\] classseparator2\<\>関数<br /><br /> \<separator1 は\> ネイティブ コードの `::`、およびマネージ コードの `.` です。<br /><br /> \<separator2 `::`\> は常になります。<br /><br /> ワイルドカード文字 \* がサポートされています。  たとえば、名前空間のすべての関数を含めるには、次を使用します。<br /><br /> MyNamespace::\*<br /><br /> **VSInstr \/DumpFuncs** を使用して、指定したバイナリの関数の完全な名前を一覧表示できます。|  
|**DumpFuncs**|指定したイメージ内の関数を一覧表示します。  インストルメンテーションは実行されません。|  
|**ExcludeSmallFuncs**|小規模関数 \(関数呼び出しを行わない短い関数\) をインストルメンテーションから除外します。  **ExcludeSmallFuncs** オプションを指定すると、インストルメンテーション オーバーヘッドが軽減するため、インストルメンテーションの速度が向上します。<br /><br /> 小規模関数を除外すると、.vsp ファイルのサイズが小さくなり、分析に要する時間も短くなります。|  
|**Mark:**{**Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom**}`,funcname,markid`|.vsp レポート ファイル内のデータ範囲の先頭または末尾を識別するために使用できるプロファイル マーク \(レポート内のデータを区切るために使用する識別子\) を挿入します。<br /><br /> **Before**  `` \- 対象の関数に入る直前。<br /><br /> **After**  `` \- 対象の関数が終了した直後。<br /><br /> **Top**  `` \- 対象の関数に入った直後。<br /><br /> **Bottom**  `` \- 対象の関数で制御が戻る直前。<br /><br /> `funcname` \- 対象の関数の名前です。<br /><br /> `Markid` \- プロファイル マークの識別子として使用する正の整数 \(long\)。|  
|**Coverage**|カバレッジ インストルメンテーションを実行します。  これは、**Verbose**、**OutputPath**、**Exclude**、および **Logfile** のオプションとのみ使用できます。|  
|**Verbose**|**Verbose** オプションは、インストルメンテーション プロセスに関する詳細情報を表示するために使用します。|  
|**NoWarn** `[:[Message Number[;Message Number]]]`|すべてまたは特定の警告を抑制します。<br /><br /> `Message Number` \- 警告番号です。  `Message Number` を省略した場合、すべての警告が出力されなくなります。<br /><br /> 詳細については、「[VSInstr の警告](../profiling/vsinstr-warnings.md)」を参照してください。|  
|**Control** `:{` **Thread** `&#124;`  **Process** `&#124;` **Global** `}`|次の VSInstr データ収集制御オプションのプロファイリング レベルを指定します。<br /><br /> **Start**<br /><br /> **StartOnly**<br /><br /> **Suspend**<br /><br /> **StopOnly**<br /><br /> **SuspendOnly**<br /><br /> **ResumeOnly**<br /><br /> **Thread**  ``  \- スレッド レベルのデータ収集制御関数を指定します。  プロファイリングは、現在のスレッドに対してのみ開始または停止されます。  他のスレッドのプロファイリング状態は影響を受けません。  既定値は thread です。<br /><br /> **Process**  `` \- プロセス レベルのプロファイリング データ収集制御関数を指定します。  プロファイリングは、現在のプロセスのすべてのスレッドに対して開始または停止されます。  他のプロセスのプロファイリング状態は影響を受けません。<br /><br /> **Global**  `` \- グローバル レベル \(プロセス間\) のデータ収集制御関数を指定します。<br /><br /> プロファイリング レベルを指定しなかった場合は、エラーが発生します。|  
|**Start** `:{` **Inside** `&#124;` **Outside** `},funcname`|データ収集を対象の関数とその関数から呼び出される子関数に制限します。<br /><br /> **Inside**  `` \- 対象の関数に入った直後に StartProfile 関数を挿入します。  対象の関数で制御が戻る直前に StopProfile 関数を挿入します。<br /><br /> **Outside**  `` \- 対象の関数をそれぞれ呼び出す直前に StartProfile 関数を挿入します。  対象の関数をそれぞれ呼び出した直後に StopProfile 関数を挿入します。<br /><br /> `funcname` \- 対象の関数の名前です。|  
|**Suspend** `:{` **Inside** `&#124;` **Outside** `},funcname`|対象の関数とその関数から呼び出される子関数に対するデータ収集を除外します。<br /><br /> **Inside**  `` \- 対象の関数に入った直後に SuspendProfile 関数を挿入します。  対象の関数で制御が戻る直前に ResumeProfile 関数を挿入します。<br /><br /> **Outside**  `` \- 対象の関数に入る直前に SuspendProfile 関数を挿入します。  対象の関数が終了した直後に ResumeProfile 関数を挿入します。<br /><br /> `funcname` \- 対象の関数の名前です。<br /><br /> 対象の関数に StartProfile 関数が含まれている場合は、SuspendProfile 関数がその前に挿入されます。  対象の関数に StopProfile 関数が含まれている場合は、ResumeProfile 関数がその後に挿入されます。|  
|**StartOnly:** `{` **Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom** `},funcname`|プロファイリング実行中にデータ収集を開始します。  このオプションは、StartProfile API 関数を指定の位置に挿入します。<br /><br /> **Before**  `` \- 対象の関数に入る直前。<br /><br /> **After**  `` \- 対象の関数が終了した直後。<br /><br /> **Top**  `` \- 対象の関数に入った直後。<br /><br /> **Bottom**  `` \- 対象の関数で制御が戻る直前。<br /><br /> `funcname` \- 対象の関数の名前です。|  
|**StopOnly:**{**Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom**}`,funcname`|プロファイリング実行中にデータ収集を停止します。  このオプションは、StopProfile 関数を指定の位置に挿入します。<br /><br /> **Before**  `` \- 対象の関数に入る直前。<br /><br /> **After**  `` \- 対象の関数が終了した直後。<br /><br /> **Top**  `` \- 対象の関数に入った直後。<br /><br /> **Bottom**  `` \- 対象の関数で制御が戻る直前。<br /><br /> `funcname` \- 対象の関数の名前です。|  
|**SuspendOnly:**{**Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom**}`,funcname`|プロファイリング実行中にデータ収集を停止します。  このオプションは、SuspendProfile API 関数を指定の位置に挿入します。<br /><br /> **Before**  `` \- 対象の関数に入る直前。<br /><br /> **After**  `` \- 対象の関数が終了した直後。<br /><br /> **Top**  `` \- 対象の関数に入った直後。<br /><br /> **Bottom**  `` \- 対象の関数で制御が戻る直前。<br /><br /> `funcname` \- 対象の関数の名前です。<br /><br /> 対象の関数に StartProfile 関数が含まれている場合は、SuspendProfile 関数がその前に挿入されます。|  
|**ResumeOnly:**{**Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom**}`,funcname`|プロファイリング実行中にデータ収集を開始または再開します。<br /><br /> 通常、このオプションは、**SuspendOnly** オプションによってプロファイリングが停止された後にプロファイリングを再開するために使用します。  このオプションは、ResumeProfile API 関数を指定の位置に挿入します。<br /><br /> **Before**  `` \- 対象の関数に入る直前。<br /><br /> **After**  `` \- 対象の関数が終了した直後。<br /><br /> **Top**  `` \- 対象の関数に入った直後。<br /><br /> **Bottom**  `` \- 対象の関数で制御が戻る直前。<br /><br /> `funcname` \- 対象の関数の名前です。<br /><br /> 対象の関数に StopProfile 関数が含まれている場合は、ResumeProfile 関数がその後に挿入されます。|  
  
## 参照  
 [VSPerfMon](../profiling/vsperfmon.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [VSPerfReport](../profiling/vsperfreport.md)   
 [VSInstr の警告](../profiling/vsinstr-warnings.md)   
 [プロファイル ツールのレポート ビュー](../profiling/performance-report-views.md)