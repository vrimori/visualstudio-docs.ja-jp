---
title: "MODULE_SYMBOL_SEARCH_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MODULE_SYMBOL_SEARCH_INFO"
helpviewer_keywords: 
  - "MODULE_SYMBOL_SEARCH_INFO 構造体"
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# MODULE_SYMBOL_SEARCH_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

検索したシンボルの検索パスに関するステータス情報が含まれています。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
typedef struct _tagSYMBOL_SEARCH_INFO  
{  
   SYMBOL_SEARCH_INFO_FIELDS dwValidFields;  
   BSTR                      bstrVerboseSearchInfo;  
} MODULE_SYMBOL_SEARCH_INFO;  
```  
  
```c#  
public struct MODULE_SYMBOL_SEARCH_INFO {  
   public uint   dwValidFields;  
   public string bstrVerboseSearchInfo;  
}  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwValidFields`  
 フラグの組み合わせ、 [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) この構造体で説明した検索情報の種類を指定する列挙体です。  
  
 `bstrVerboseSearchInfo`  
 検索パスと 1 つの文字列の連結結果。  
  
## <a name="remarks"></a>解説  
 この構造体がへの呼び出しから返される、 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) メソッドです。  
  
 場合、 `bstrVerboseSearchInfo` フィールドが空ではありませんし、検索するパスと検索結果の一覧が含まれています。 一覧には、省略記号 (「...」)、結果の後に続く、パスが表示されます。 1 つ以上のパスの結果のペアがある場合は、各ペアは"\r\n"(キャリッジ リターン/改行) の組み合わせによって区切られます。 パターンは、次のようになります。  
  
 \< パス>... \< 結果>\r\n \< パス>... \< 結果>\r\n \< パス>... \< 結果>  
  
 最後のエントリに \r\n シーケンスがないことに注意してください。  
  
 ここでは、できるだけ `bstrVerboseSearchInfo` 標準出力に送信された文字列。  
  
 `c:\symbols\user32.pdb... File not found.`  
  
 `c:\winnt\symbols\user32.pdb... Version does not match.`  
  
 `\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)