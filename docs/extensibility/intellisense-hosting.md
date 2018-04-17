---
title: IntelliSense をホストしている |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - IntelliSense hosting
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b101460b3867c89862068d99412cd06edb884ef7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="intellisense-hosting"></a>IntelliSense をホストしています。
Visual Studio では IntelliSense をホストします。 ホストにより IntellSense IntelliSense を Visual Studio テキスト エディターによってホストされていないコードを提供します。  
  
## <a name="intellisense-hosting-usage"></a>ホスト使用率の IntelliSense  
 Visual Studio で、入力候補のセットとテキスト バッファーにアクセスするすべてのコードは、どこからでも IntelliSense ウィンドウを取得できます、ユーザー インターフェイス (UI) にします。 このシナリオ例で補完、**ウォッチ**ウィンドウやブレークポイントのプロパティ ウィンドウの 状態 フィールドにします。  
  
### <a name="implementation-interfaces"></a>実装インターフェイス  
  
#### <a name="ivsintellisensehost"></a>IVsIntellisenseHost  
 IntelliSense のポップアップ ウィンドウをホストしている UI コンポーネントをサポートする必要があります、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>インターフェイスです。 既定のコア エディターのテキスト ビューには、株式が含まれています。<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>インターフェイスの現在の IntelliSense 機能を保持する実装。 ほとんどの場合、メソッド、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>表しますに新機能のサブセットを実装するインターフェイス、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>インターフェイスです。 サブセットには、IntelliSense UI 処理、カレット、選択操作、および単純なテキストの置換機能が含まれています。 さらに、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>インターフェイスを使用する別の IntelliSense"subject"および「コンテキスト」コンテキストが使用されているテキスト バッファーに直接存在しないのサブジェクトは、IntelliSense を提供できるようにします。  
  
#### <a name="ivsintellisensehostgethostflags"></a>IVsIntellisenseHost.GetHostFlags  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>プロバイダーのインターフェイスを実装する必要があります、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> IntelliSense の種類、ホストの機能を決定するクライアントを有効にするメソッドをサポートしています。  
  
 定義されているホスト フラグは、 [IntelliSenseHostFlags](../extensibility/intellisensehostflags.md)、以下にまとめます。  
  
|IntelliSense ホスト フラグ|説明|  
|----------------------------|-----------------|  
|IHF_READONLYCONTEXT|読み取り専用と編集が、件名のテキスト内でのみが発生したフラグつまりコンテキスト バッファーを設定します。|  
|IHF_NOSEPERATESUBJECT|設定このフラグは、意味がある別の IntelliSense サブジェクトはありません。 サブジェクトに存在するコンテキスト バッファーなど、従来の<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>IntelliSense システムです。|  
|IHF_SINGLELINESUBJECT|設定のサブジェクトがないフラグとは、こので、編集可能な 1 行のようにこのような複数行、**ウォッチ**ウィンドウです。|  
|IHF_FORCECOMMITTOCONTEXT|このフラグが設定されてとコンテキスト バッファーを更新する必要があります、ホストによって、読み取り専用フラグを無視するように、コンテキスト バッファーと編集を続行します。|  
|IHF_OVERTYPE|(サブジェクトまたはコンテキスト) での編集は、上書きモードで行う必要があります。|  
  
#### <a name="ivsintellisensehostbeforecompletorcommit-and-ivsintellisensehostaftercompletorcommit"></a>IVsIntellisenseHost.BeforeCompletorCommit と IVsIntellisenseHost.AfterCompletorCommit  
 これらのコールバック メソッドは、前に、およびテキストは、前処理と後処理を有効にコミットされた後に補完ウィンドウによって呼び出されます。  
  
#### <a name="ivsintellisensecompletor"></a>IVsIntellisenseCompletor  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor>インターフェイスは、統合開発環境 (IDE) で使用される標準の補完ウィンドウの共同作成可能なバージョンです。 どの<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>インターフェイスがこの completor インターフェイスを使用して IntelliSense を簡単に実装できます。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.TextManager.Interop>