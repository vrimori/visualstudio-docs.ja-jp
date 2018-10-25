---
title: ポートへの通知 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3a45882b1410391843b9e98dcce6e963774c15dd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49868301"
---
# <a name="notify-the-port"></a>ポートへの通知します。
プログラムを起動した後、ポートに通知する、次のように。  
  
1. ポートは、プログラムの新しいノードを受信すると、デバッグ セッションに戻るプログラムの作成イベントを送信します。 イベントを伴って、プログラムを表すインターフェイスです。  
  
2. デバッグ セッションにアタッチできるデバッグ エンジン (DE) の識別子のプログラムを照会します。  
  
3. デバッグ セッションは、そのプログラムの許容 DEs の一覧に、DE があるかを確認します。 デバッグ セッションは、ソリューションのアクティブなプログラムの設定、デバッグ パッケージによってを最初に渡されたからこの一覧を取得します。  
  
    許可の一覧で、DE 必要があります。 そう、DE、プログラムにアタッチされません。  
  
   プログラムでは、ポートは、プログラムの新しいノードを最初に受信すると、作成、 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)をプログラムを表すインターフェイス。  
  
> [!NOTE]
>  これと混同しないで、`IDebugProgram2`デバッグ エンジン (DE) によって後で作成されたインターフェイスです。  
  
 ポートの送信、 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) COM を使用してセッション デバッグ マネージャー (SDM) にプログラムの作成イベント`IConnectionPoint`インターフェイス。  
  
> [!NOTE]
>  これは、必要がありますと混同しない、`IDebugProgramCreateEvent2`インターフェイス、DE、後で送信されます。  
  
 ポートの送信イベント インターフェイス自体と共に、 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)、 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)、および[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)インターフェイス、ポートを表し、処理、およびプログラム、それぞれします。 SDM コール[IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)プログラムをデバッグできる DE の GUID を取得します。 GUID がから最初に取得された、 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)インターフェイス。  
  
 SDM は、DE が許容 DEs の一覧にあるかを確認します。 SDM は、ソリューションのアクティブなプログラムの設定、デバッグ パッケージによってを最初に渡されたからこの一覧を取得します。 許可の一覧で、DE 必要があります。 そうしないプログラムにアタッチされません。  
  
 デの id がわかったら、SDM は、プログラムにアタッチする準備ができてです。  
  
## <a name="see-also"></a>関連項目  
 [プログラムの起動](../../extensibility/debugger/launching-a-program.md)   
 [起動後のアタッチ](../../extensibility/debugger/attaching-after-a-launch.md)   
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)