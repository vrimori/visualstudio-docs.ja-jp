---
title: COMPUTER_INFO |Microsoft ドキュメント
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
ms.openlocfilehash: 0f9f81532608a4919707b5acafbde7ce1d8fe400
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102042"
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
 オペレーティング システムのバージョン番号です。  
  
## <a name="remarks"></a>コメント  
 この構造体は、によって返される、 [GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)メソッドです。  
  
## <a name="requirements"></a>要件  
 ヘッダー: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)