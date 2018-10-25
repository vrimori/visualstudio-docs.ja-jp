---
title: CONNECTION_PROTOCOL |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d70aa31e7574e9fcdb0ed4e8d89847e832f3739b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832771"
---
# <a name="connectionprotocol"></a>CONNECTION_PROTOCOL
デバッグ サーバーとパッケージのデバッグ (DE) 間の通信に使用されるプロトコルを示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum tagCONNECTION_PROTOCOL {  
   CONNECTION_NONE    = 0,  
   CONNECTION_UNKNOWN = 1,  
   CONNECTION_LOCAL   = 2,  
   CONNECTION_PIPE    = 3,  
   CONNECTION_TCPIP   = 4,  
   CONNECTION_HTTP    = 5,  
   CONNECTION_OTHER   = 6  
} CONNECTION_PROTOCOL;  
```  
  
```csharp  
public enum CONNECTION_PROTOCOL {  
   CONNECTION_NONE    = 0,  
   CONNECTION_UNKNOWN = 1,  
   CONNECTION_LOCAL   = 2,  
   CONNECTION_PIPE    = 3,  
   CONNECTION_TCPIP   = 4,  
   CONNECTION_HTTP    = 5,  
   CONNECTION_OTHER   = 6  
};  
```  
  
#### <a name="parameters"></a>パラメーター  
 CONNECTION_NONE  
 サーバーに接続が確立されていません。  
  
 CONNECTION_UNKNOWN  
 接続が確立されていますが、不明な型のです。  
  
 CONNECTION_LOCAL  
 ローカル サーバーへの接続です。  
  
 CONNECTION_PIPE  
 接続では、名前付きパイプ経由です。  
  
 CONNECTION_TCPIP  
 接続は、TCP/IP を使用します。  
  
 CONNECTION_HTTP  
 接続は、(Web サーバー) 経由の HTTP を使用します。  
  
 CONNECTION_OTHER  
 他の種類の接続が確立されています (この値は現在使用されません)。  
  
## <a name="remarks"></a>Remarks  
 これらの値から返される、 [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)メソッド。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)