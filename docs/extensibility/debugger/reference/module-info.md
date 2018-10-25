---
title: MODULE_INFO |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- MODULE_INFO
helpviewer_keywords:
- MODULE_INFO structure
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b28770482357b7e006793f15438e7880f7efb1ec
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897005"
---
# <a name="moduleinfo"></a>MODULE_INFO
特定のモジュール (DLL、exe ファイルまたはアセンブリ) について説明します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct tagMODULE_INFO {   
   MODULE_INFO_FIELDS dwValidFields;  
   BSTR               m_bstrName;  
   BSTR               m_bstrUrl;  
   BSTR               m_bstrVersion;  
   BSTR               m_bstrDebugMessage;  
   UINT64             m_addrLoadAddress;  
   UINT64             m_addrPreferredLoadAddress;  
   DWORD              m_dwSize;  
   DWORD              m_dwLoadOrder;  
   FILETIME           m_TimeStamp;  
   BSTR               m_bstrUrlSymbolLocation;  
   MODULE_FLAGS       m_dwModuleFlags;  
} MODULE_INFO;  
```  
  
```csharp  
public struct MODULE_INFO {   
   public uint     dwValidFields;  
   public string   m_bstrName;  
   public string   m_bstrUrl;  
   public string   m_bstrVersion;  
   public string   m_bstrDebugMessage;  
   public ulong    m_addrLoadAddress;  
   public ulong    m_addrPreferredLoadAddress;  
   public uint     m_dwSize;  
   public uint     m_dwLoadOrder;  
   public FILETIME m_TimeStamp;  
   public string   m_bstrUrlSymbolLocation;  
   public uint     m_dwModuleFlags;  
};  
```  
  
## <a name="members"></a>メンバー  
 dwValidFields  
 フラグの組み合わせ、 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)フィールドが記入を指定する列挙体。  
  
 m_bstrName  
 モジュール名。  
  
 m_bstrUrl  
 モジュールの URL。  
  
 m_bstrVersion  
 モジュールのバージョン。  
  
 m_bstrDebugMessage  
 オプションのメッセージ、モジュールに関するなど「シンボルを読み込めません」  
  
 m_addrLoadAddress  
 モジュールの読み込みアドレス。  
  
 m_addrPreferredLoadAddress  
 モジュールの標準読み込みアドレス。  
  
 m_dwSize  
 モジュールのサイズ。  
  
 m_dwLoadOrder  
 モジュールの読み込み順序。  
  
 m_TimeStamp  
 シンボル ファイルの最終変更時刻。  
  
 m_bstrUrlSymbolLocation  
 シンボル ファイルの場所 (たとえば、".\\")、モジュールで指定します。 開始位置として、モジュールのシンボルを検索するために使用します。  
  
 m_dwModuleFlags  
 フラグの組み合わせ、 [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)モジュールを表す列挙体。  
  
## <a name="remarks"></a>Remarks  
 この構造体に渡される、 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)メソッドでいっぱいになった場所。  
  
 この構造で表示されている各モジュールに対応する、**モジュール**ウィンドウ。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)