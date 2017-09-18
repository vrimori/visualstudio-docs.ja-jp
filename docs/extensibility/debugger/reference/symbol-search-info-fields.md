---
title: "SYMBOL_SEARCH_INFO_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SYMBOL_SEARCH_INFO_FIELDS"
helpviewer_keywords: 
  - "SYMBOL_SEARCH_INFO_FIELDS 列挙型"
ms.assetid: bce35af0-722d-46d4-afa6-eaae598c51ff
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# SYMBOL_SEARCH_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

シンボル情報の種類を取得するように指定します。  
  
## 構文  
  
```cpp#  
enum enum_SYMBOL_SEARCH_INFO_FIELDS  
{  
   SSIF_NONE                = 0x00000000,  
   SSIF_VERBOSE_SEARCH_INFO = 0x00000001  
};  
typedef DWORD SYMBOL_SEARCH_INFO_FIELDS;  
```  
  
```c#  
public enum enum_SYMBOL_SEARCH_INFO_FIELDS  
{  
   SSIF_NONE                = 0x00000000,  
   SSIF_VERBOSE_SEARCH_INFO = 0x00000001  
};  
  
```  
  
## メンバー  
 SSIF\_NONE  
 フラグは表示されません。  
  
 SSIF\_VERBOSE\_SEARCH\_INFO  
 シンボルを検索するために使用されるすべての検索パスを返します  
  
## 解説  
 これらのフラグは [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) のメソッドにパラメーターとして返される情報の量を確認するために渡されます。  
  
> [!NOTE]
>  現在`SSIF_VERBOSE_SEARCH_INFO` のみサポートされ`IDebugModule3::GetSymbolInfo` への `dwFlags` のパラメーターとして指定する必要があります。  他のすべての値はエラーを返します。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)