---
title: SYMBOL_SEARCH_INFO_FIELDS |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SYMBOL_SEARCH_INFO_FIELDS
helpviewer_keywords:
- SYMBOL_SEARCH_INFO_FIELDS enumeration
ms.assetid: bce35af0-722d-46d4-afa6-eaae598c51ff
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dac1234a765bbb3064ea4471d7531864306e0220
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49842925"
---
# <a name="symbolsearchinfofields"></a>SYMBOL_SEARCH_INFO_FIELDS
取得するシンボル情報の種類を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_SYMBOL_SEARCH_INFO_FIELDS  
{  
   SSIF_NONE                = 0x00000000,  
   SSIF_VERBOSE_SEARCH_INFO = 0x00000001  
};  
typedef DWORD SYMBOL_SEARCH_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_SYMBOL_SEARCH_INFO_FIELDS  
{  
   SSIF_NONE                = 0x00000000,  
   SSIF_VERBOSE_SEARCH_INFO = 0x00000001  
};  
  
```  
  
## <a name="members"></a>メンバー  
 SSIF_NONE  
 フラグがないことを示します。  
  
 SSIF_VERBOSE_SEARCH_INFO  
 すべての検索シンボルを検索するために使用されるパスを返します。  
  
## <a name="remarks"></a>Remarks  
 これらのフラグは、パラメーターとして渡される、 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)情報の量を判断するメソッドが返されます。  
  
> [!NOTE]
>  現時点では、のみ`SSIF_VERBOSE_SEARCH_INFO`はサポートされていることを指定する必要があります、`dwFlags`パラメーターを`IDebugModule3::GetSymbolInfo`します。 その他のすべての値は、エラーを返します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)