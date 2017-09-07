---
title: "CONNECTION_PROTOCOL |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 2be5678704e9a5899c4ce7f5caba8cec1d8a21e6
ms.contentlocale: ja-jp
ms.lasthandoff: 09/06/2017

---
# CONNECTION_PROTOCOL
デバッグ サーバーとデバッグ パッケージ (DE) 間の通信に使用されているプロトコルを示します。  
  
## 構文  
  
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
  
#### パラメーター  
 CONNECTION_NONE  
 サーバーに接続が確立したありません。  
  
 CONNECTION_UNKNOWN  
 接続が確立されましたが、不明な種類のします。  
  
 CONNECTION_LOCAL  
 ローカル サーバーへの接続です。  
  
 CONNECTION_PIPE  
 名前付きパイプは接続です。  
  
 CONNECTION_TCPIP  
 接続には、TCP/IP が使用されます。  
  
 CONNECTION_HTTP  
 接続は、(Web サーバー) を介して、HTTP を使用します。  
  
 CONNECTION_OTHER  
 その他の何らかの種類の接続が確立された (この値は現在使用されません)。  
  
## コメント  
 これらの値から返される、 [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)メソッドです。  
  
## 要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)
