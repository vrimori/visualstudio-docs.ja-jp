---
title: MODULE_SYMBOL_SEARCH_INFO |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9deadc13f8cbe3678282bb2d9ac619959ecd26b3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49875919"
---
# <a name="modulesymbolsearchinfo"></a>MODULE_SYMBOL_SEARCH_INFO
検索したシンボルの検索パスに関するステータス情報が含まれています。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _tagSYMBOL_SEARCH_INFO  
{  
   SYMBOL_SEARCH_INFO_FIELDS dwValidFields;  
   BSTR                      bstrVerboseSearchInfo;  
} MODULE_SYMBOL_SEARCH_INFO;  
```  
  
```csharp  
public struct MODULE_SYMBOL_SEARCH_INFO {  
   public uint   dwValidFields;  
   public string bstrVerboseSearchInfo;  
}  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwValidFields`  
 フラグの組み合わせ、 [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)この構造体で表される検索情報の種類を指定する列挙体。  
  
 `bstrVerboseSearchInfo`  
 検索パスと 1 つの文字列に連結された結果。  
  
## <a name="remarks"></a>Remarks  
 この構造体がへの呼び出しから返される、 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)メソッド。  
  
 場合、`bstrVerboseSearchInfo`フィールドが空ではありませんし、検索するパスと検索結果の一覧が含まれています。 一覧には、後ろに省略記号 (「...」)、結果の後に、パスが表示されます。 1 つ以上のパスの結果のペアがある場合は、各ペアは"\r\n"(復帰と改行) のペアによって区切られます。 パターンのようになります。  
  
 \<パス >.\<結果 > \r\n\<パス >.\<結果 > \r\n\<パス >.\<結果 >  
  
 最後のエントリに \r\n シーケンスがないことに注意してください。  
  
 ここでは、する可能性のある`bstrVerboseSearchInfo`を標準出力に送信された文字列。  
  
 `c:\symbols\user32.pdb... File not found.`  
  
 `c:\winnt\symbols\user32.pdb... Version does not match.`  
  
 `\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)