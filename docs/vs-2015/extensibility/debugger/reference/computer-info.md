---
title: COMPUTER_INFO |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- COMPUTER_INFO structure
ms.assetid: 943085b2-f165-462d-9a4e-2086f0cdfff4
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0309a3406b4b72c5a56a3c727ad21b165573674d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49203581"
---
# <a name="computerinfo"></a>COMPUTER_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

デバッガーが実行されているコンピューターをについて説明します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
  
## <a name="requirements"></a>要件  
 ヘッダー: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)

