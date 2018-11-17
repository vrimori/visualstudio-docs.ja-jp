---
title: ポートへの通知 |Microsoft Docs
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
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c3cfcc4ee357301aa0e38468b13b983c3d5ca55a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51763371"
---
# <a name="notifying-the-port"></a>ポートへの通知
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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

