---
title: "方法: エディターのコンテキストを指定 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: d9b89c4e45f8268df55386d321816325fb50174c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-provide-context-for-editors"></a>方法: エディターのコンテキストを指定
エディターのコンテキストはアクティブなエディターにフォーカスがあるか、ツール ウィンドウにフォーカスが移動された直前にフォーカスがあった場合にのみです。 次の手順を実行して、エディターのコンテキストを指定できます。  
  
1.  コンテキストのバッグを作成します。  
  
2.  選択範囲の要素の識別子 (SEID) に、コンテキストのバッグを発行します。  
  
3.  バッグにコンテキストを維持します。  
  
 次の手順では、これらのタスクについて説明します。 詳細については、コンテキストを提供する、次を参照してください。**信頼性の高いプログラミング**このトピックで後述します。  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>エディターまたはデザイナーのコンテキストのバッグを作成するには  
  
1.  呼び出す`QueryService`上、<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>のためのインターフェイス、<xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext>サービス。  
  
     ポインター、<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext>インターフェイスが返されます。  
  
2.  呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A>メソッドを新しいコンテキストまたはサブコンテキスト バッグを作成します。  
  
     ポインター、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>インターフェイスが返されます。  
  
3.  呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>コンテキストまたはサブコンテキスト バッグに、属性、lookup キーワード、または F1 キーワードを追加します。  
  
4.  サブコンテキスト バッグを作成する場合は、呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A>サブコンテキスト バッグを親コンテキスト バッグにリンクする方法です。  
  
5.  呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>通知を受信するときに、**ダイナミック ヘルプ**ウィンドウが更新しようとしています。  
  
     持つ、**ダイナミック ヘルプ**ウィンドウ、エディターを呼び出す更新が発生するまで、コンテキストを変更する操作を遅らせることができますを更新する準備ができます。 これを行うと、システムのアイドル時間が利用可能になるまでに時間がかかるアルゴリズムを実行しているを遅延することができますのでパフォーマンスを向上できます。  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>コンテキストのバッグを SEID に発行するには  
  
1.  呼び出す`QueryService`上、<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>サービスへのポインターを返します、<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>インターフェイスです。  
  
2.  呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>、要素の識別子を指定する (`elementid`パラメーター)、グローバル レベルにコンテキストを渡すことを示すために SEID_UserContext の値。  
  
3.  内の値、ときに、エディターまたはデザイナーがアクティブになったその<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>オブジェクトは、グローバルの選択に反映されます。 セッションごとに 1 回、このプロセスを完了しが呼び出されたときに作成されたグローバル コンテキストへのポインターを格納するだけ済みます<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>です。  
  
### <a name="to-maintain-the-context-bag"></a>コンテキストのバッグを維持するために  
  
1.  実装<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>ことを確認する、**ダイナミック ヘルプ** ウィンドウの呼び出し、エディターまたはデザイナーの更新前にします。  
  
     呼び出された各コンテキスト バッグに<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>コンテキスト バッグが作成され、インプリメント後<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>、IDE 呼び出し<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>コンテキスト プロバイダー コンテキスト バッグが更新されることを通知します。 この呼び出しを使用するには属性とキーワード コンテキスト バッグ、および任意サブコンテキスト バッグを前に変更する、**ダイナミック ヘルプ**ウィンドウの更新が発生します。  
  
2.  呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>エディターまたはデザイナーが新しいコンテキストを持つことを示すためにコンテキスト バッグにします。  
  
     ときに、**ダイナミック ヘルプ**ウィンドウ呼び出し<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>を示すことが更新中、エディターまたはデザイナーは、その時点で、親のコンテキストのバッグと任意サブコンテキスト バッグの両方の適切なコンテキストを更新できます。  
  
    > [!NOTE]
    >  `SetDirty`フラグが自動的に設定`true`コンテキストが追加またはコンテキスト バッグから削除されるたびにします。 **ダイナミック ヘルプ** ウィンドウの呼び出しのみ<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>コンテキスト バッグの場合、`SetDirty`にフラグが設定されている`true`です。 リセット`false`の更新の後です。  
  
3.  呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>コンテキストのアクティブなコレクションにコンテキストを追加するか、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>コンテキストを削除します。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 独自のエディターを作成している場合は、3 つすべてのエディターのコンテキストを提供するには、このトピックの手順を完了する必要があります。  
  
> [!NOTE]
>  適切なエディターまたはデザイナー ウィンドウをアクティブ化し、更新されるようにするコマンド ルーティングが正常に呼び出す必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>フォーカス ウィンドウを作成するコンポーネントです。  
  
 SEID は、選択内容に基づいて変更されるプロパティのコレクションです。 SEID 情報は、グローバルの選択しています。 によってトリガーされるイベントに、グローバルの選択がワイヤード (有線)、<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>インターフェイスがあるすべての項目のリスト選択されている (現在のエディター、現在のツール ウィンドウ、現在の階層、およびなど)。  
  
 エディターとデザイナーでは、コンテキストをするたびに変更できますで、カーソルが移動、単語内にあるコンテキスト バッグを絶えず更新効率的ではありません。 効率的なエディターまたはデザイナー ウィンドウ内での移動のカーソルを検出する任意の時間を更新するには、呼び出すことができます<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>です。 それにより、アイドル状態の時間があるし、エディターまたはデザイナーに IDE のコンテキストのサービスは通知を送信するまで、コンテキストの変更を保持するために、**ダイナミック ヘルプ**ウィンドウを更新します。 この方法は、このトピックのコンテキストのバッグの管理"するには」手順で使用されます。  
  
 エディターまたはデザイナー内のアクティビティ コンテキストを提供すると、エディターまたはデザイナー自体のヘルプを表示するユーザーを許可する特定の F1 キーワードを指定する必要があります。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>