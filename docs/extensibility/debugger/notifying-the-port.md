---
title: ポートへの通知 |Microsoft ドキュメント
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
ms.openlocfilehash: 1420ca8768ddf1eaedc0d515810bc88b3491c4db
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31101262"
---
# <a name="notifying-the-port"></a>ポートを通知します。
プログラムを開始した後に、ポート必要がありますには通知とおり。  
  
1.  ポートは、新しいプログラム ノードを受信すると、デバッグ セッションに戻るプログラム作成イベントを送信します。 イベントは、それにプログラムを表すインターフェイスを実行します。  
  
2.  デバッグ セッションは、デバッグ エンジン (DE) にアタッチできるの識別子のプログラムを照会します。  
  
3.  デバッグ セッションは、DE が許容される DEs でそのプログラムの一覧にかどうかを確認します。 デバッグ セッションは、デバッグ パッケージによってを最初に渡されたソリューションのアクティブなプログラムの設定から、この一覧を取得します。  
  
     許可のリストにする必要があります、DE しない場合、DE、プログラムにアタッチされません。  
  
 プログラムでは、ポート最初に受信すると、新しいプログラム ノードを作成、 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)プログラムを表すインターフェイス。  
  
> [!NOTE]
>  これがないと混同しないでください、`IDebugProgram2`デバッグ エンジン (DE) によって後で作成されるインターフェイス。  
  
 ポートの送信、 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) COM を使用してセッション デバッグ マネージャー (SDM) にプログラムの作成イベント`IConnectionPoint`インターフェイスです。  
  
> [!NOTE]
>  これがないと混同しないでください、`IDebugProgramCreateEvent2`デによって後で送信されるインターフェイス。  
  
 ポートの送信イベント インターフェイス自体と共に、 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)、 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)、および[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)インターフェイスで、ポートを表す、処理、およびプログラム、それぞれします。 SDM 呼び出し[IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)プログラムをデバッグできる DE の GUID を取得します。 GUID がから最初に取得された、 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)インターフェイスです。  
  
 SDM はかどうか、DE は許容 DEs の一覧を確認します。 SDM は、デバッグ パッケージによってを最初に渡されたソリューションのアクティブなプログラムの設定から、この一覧を取得します。 デが、許可リストにする必要があります。 追加しないプログラムにアタッチされません。  
  
 デの id が認識されたら、SDM はプログラムにアタッチする準備ができてです。  
  
## <a name="see-also"></a>関連項目  
 [プログラムの起動](../../extensibility/debugger/launching-a-program.md)   
 [起動後にアタッチします。](../../extensibility/debugger/attaching-after-a-launch.md)   
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)