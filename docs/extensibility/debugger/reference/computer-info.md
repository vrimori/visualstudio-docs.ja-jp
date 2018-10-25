---
title: COMPUTER_INFO |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- COMPUTER_INFO structure
ms.assetid: 943085b2-f165-462d-9a4e-2086f0cdfff4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9a52247f36f3628d91e83a89ded88a35c6ee8e68
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49864219"
---
# <a name="computerinfo"></a>COMPUTER_INFO
デバッガーが実行されているコンピューターをについて説明します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct tagCOMPUTER_INFO  
{  
    WORD wProcessorArchitecture;  
    WORD wSuiteMask;  
    DWORD dwOperatingSystemVersion;  
} COMPUTER_INFO;  
```  
  
```csharp  
public struct COMPUTER_INFO  
{  
    public ushort wProcessorArchitecture;  
    public ushort wSuiteMask;  
    public uint dwOperatingSystemVersion;  
}  
```  
  
## <a name="terms"></a>用語  
 wProcessorArchitecture  
 マイクロプロセッサのアーキテクチャを識別します。  
  
 wSuiteMask  
 スイートのマスクを識別します。  
  
 dwOperatingSystemVersion  
 オペレーティング システムのバージョン番号。  
  
## <a name="remarks"></a>Remarks  
 この構造体がによって返される、 [GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)メソッド。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)