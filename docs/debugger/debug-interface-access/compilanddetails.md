---
title: CompilandDetails |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1325d32c3656a45cab41bd174596113a18c5f58c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53936907"
---
# <a name="compilanddetails"></a>CompilandDetails
コンパイル単位の情報を使用したシンボルに分割されて、`SymTagCompiland`タグ (解像度の低い) と`SymTagCompilandDetails`タグ (詳細)。 `SymTagCompilandDetails` 追加のシンボルを読み込む必要があります。 ただしは、豊富な情報では利用できませんが、コンパイル単位について、`SymTagCompiland`シンボル。  
  
## <a name="properties"></a>プロパティ  
 次の表では、この記号の型の有効なプロパティを示します。  
  
|プロパティ|データの種類|説明|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|コンパイラのバックエンドのビルド番号。|  
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|コンパイラのバック エンドのメジャー バージョン番号。|  
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|コンパイラのバック エンドのマイナー バージョン番号。|  
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|(以降でのみ DIA SDK バージョン 8.0) は、このコンパイル単位を生成するコンパイラの名前。|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` エディット コンティニュは、コンパイルで有効にされました。 場合、|  
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|コンパイラのフロント エンドのビルド番号。|  
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|コンパイラのフロント エンドのメジャー バージョン番号。|  
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|コンパイラのフロント エンドのマイナー バージョン番号。|  
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE` このコンパイル単位にデバッグ情報 (DIA SDK バージョン 8.0 でのみまたはそれ以降) がある場合。|  
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` このコンパイル単位には、マネージ コード (DIA SDK バージョン 8.0 でのみまたはそれ以降) が含まれています。 場合、|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` コンパイル単位をコンパイルした場合、 [/GS (バッファー セキュリティ チェック)](/cpp/build/reference/gs-buffer-security-check)コンパイラ スイッチ (DIA SDK バージョン 8.0 でのみまたはそれ以降)。|  
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` コンパイル単位は、共通中間言語 (CIL) コードからネイティブ コードに変換されました。 場合、|  
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` ユーザー定義型 (UDT) に整列されている場合一部がメモリ境界 (DIA SDK バージョン 8.0 でのみまたはそれ以降) に指定します。|  
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` コンパイル単位をコンパイルした場合、 [/hotpatch (ホットパッチ可能なイメージの作成)](/cpp/build/reference/hotpatch-create-hotpatchable-image)コンパイラ スイッチ (DIA SDK バージョン 8.0 でのみまたはそれ以降)。|  
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` コンパイル単位をコンパイルした場合、 [/LTCG (リンク時コード生成)](/cpp/build/reference/ltcg-link-time-code-generation)コンパイラ スイッチ (DIA SDK バージョン 8.0 でのみまたはそれ以降)。|  
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|コンパイル単位が Microsoft Intermediate Language (MSIL) モジュール (DIA SDK バージョン 8.0 でのみまたはそれ以降) の場合は TRUE。|  
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|ソース コード言語。|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|コンパイル単位の記号。|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|構文の親のシンボルの ID。|  
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|コンパイル単位がコンパイルされたプラットフォーム (の 1 つ、 [CV_CPU_TYPE_e 列挙型](../../debugger/debug-interface-access/cv-cpu-type-e.md)値)。|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|シンボルのインデックス ID。|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|返します`SymTagCompilandDetails`(の 1 つ、 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)値)。|  
  
## <a name="remarks"></a>コメント  
 コンパイラは、多くの場合、2 パス コンパイラ; と呼ばれる形式で付属します。一部のコンパイラ バージョンでは、各パスは別のプログラムによって処理されます。 これらは既知としてフロント エンドとバックエンドのコンパイラでは、それぞれ、ためバックエンドとフロント エンドのバージョン番号のシンボル プロパティ。  
  
## <a name="see-also"></a>「  
 [コンパイル単位](../../debugger/debug-interface-access/compiland.md)   
 [シンボル型の構文階層](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)