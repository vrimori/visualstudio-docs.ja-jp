---
title: "CompilandDetails | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CompilandDetails シンボル"
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CompilandDetails
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

コンパイル単位の情報は `SymTagCompiland` のタグの詳細 \(\) と `SymTagCompilandDetails` のタグの詳細 \(\) が付いたシンボルに分割されます。  `SymTagCompilandDetails` は追加のシンボルを読み込む必要があります。  ただし`SymTagCompiland` のシンボルで使用できないコンパイル単位の豊富な情報を提供します。  
  
## プロパティ  
 次の表はこのシンボルの型に対して有効なプロパティを次に示します。  
  
|プロパティ|データ型|Description|  
|-----------|----------|-----------------|  
|[IDiaSymbol::get\_backEndBuild](../Topic/IDiaSymbol::get_backEndBuild.md)|`DWORD`|コンパイラのバックエンドのビルド番号。|  
|[IDiaSymbol::get\_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|コンパイラのバックエンドのメジャー バージョン番号。|  
|[IDiaSymbol::get\_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|コンパイラのバックエンドのマイナー バージョン番号。|  
|[IDiaSymbol::get\_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|このコンパイル単位を生成するコンパイラの名前 \(DIA SDK V8.0 以降でのみ\)。|  
|[IDiaSymbol::get\_editAndContinueEnabled](../Topic/IDiaSymbol::get_editAndContinueEnabled.md)|`BOOL`|エディット コンティニュはコンパイルで有効になっている場合 `TRUE`。|  
|[IDiaSymbol::get\_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|コンパイラの以前チーム ビルド番号。|  
|[IDiaSymbol::get\_frontEndMajor](../Topic/IDiaSymbol::get_frontEndMajor.md)|`DWORD`|コンパイラのフロントエンド前メジャー バージョン番号。|  
|[IDiaSymbol::get\_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|コンパイラのフロントエンド前マイナー バージョン番号。|  
|[IDiaSymbol::get\_hasDebugInfo](../Topic/IDiaSymbol::get_hasDebugInfo.md)|`BOOL`|このコンパイル単位にデバッグ情報がある場合 `TRUE` DIA \(SDK V8.0 以降でのみ\)。|  
|[IDiaSymbol::get\_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|このコンパイル単位にマネージ コードが含まれる場合 `TRUE` DIA \(SDK v8.0 以降でのみ\)。|  
|[IDiaSymbol::get\_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|コンパイル単位を [\/GS \(バッファーのセキュリティ チェック\)](/visual-cpp/build/reference/gs-buffer-security-check) のコンパイラ スイッチを使用してコンパイル `TRUE` DIA \(SDK V8.0 以降でのみ\)。|  
|[IDiaSymbol::get\_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|共通コンパイル単位が中間言語コードからネイティブ コード \(CIL\) に変換された `TRUE`。|  
|[IDiaSymbol::get\_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|ユーザー定義型は指定 \(UDT\) されたメモリの境界に配置された `TRUE` DIA \(SDK V8.0 以降でのみ\)。|  
|[IDiaSymbol::get\_isHotpatchable](../Topic/IDiaSymbol::get_isHotpatchable.md)|`BOOL`|コンパイル単位を [\/hotpatch \(ホットパッチ可能なイメージの作成\)](/visual-cpp/build/reference/hotpatch-create-hotpatchable-image) のコンパイラ スイッチを使用してコンパイル `TRUE` DIA \(SDK v8.0 以降でのみ\)。|  
|[IDiaSymbol::get\_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|コンパイル単位を [\/LTCG \(リンク時のコード生成\)](/visual-cpp/build/reference/ltcg-link-time-code-generation) のコンパイラ スイッチを使用してコンパイル `TRUE` DIA \(SDK V8.0 以降でのみ\)。|  
|[IDiaSymbol::get\_isMSILNetmodule](../Topic/IDiaSymbol::get_isMSILNetmodule.md)|`BOOL`|コンパイル単位が Microsoft Intermediate Language \(MSIL\) モジュール True DIA \(SDK v8.0 以降でのみ\)。|  
|[IDiaSymbol::get\_language](../Topic/IDiaSymbol::get_language.md)|`DWORD`|ソース・コードの言語。|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|コンパイル単位のシンボル。|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|構文親のシンボル ID。|  
|[IDiaSymbol::get\_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|コンパイル単位がコンパイルされるプラットフォーム \([CV\_CPU\_TYPE\_e 列挙型](../../debugger/debug-interface-access/cv-cpu-type-e.md) 値のいずれか 1 つが\)。|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|シンボルのインデックスの ID。|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|`SymTagCompilandDetails` [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md) の値 \(1\) を返します。|  
  
## 解説  
 コンパイラは路式のコンパイラと呼ばれる形態 ; あるバージョンのコンパイラでは各パスが別のプログラムによって処理されます。  これらはバック エンドとチーム前バージョン番号の以前のコンパイラのフロントエンドとバックそれぞれしたがってシンボルのプロパティと呼ばれます。  
  
## 参照  
 [コンパイル単位](../../debugger/debug-interface-access/compiland.md)   
 [シンボル型の構文階層](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)