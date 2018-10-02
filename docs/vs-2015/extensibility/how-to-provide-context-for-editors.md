---
title: '方法: エディターのコンテキストを提供 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9509dfeef5af4866531af96fce6f4c1717100a94
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47546409"
---
# <a name="how-to-provide-context-for-editors"></a>方法: エディターのコンテキストを提供
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: エディターのコンテキストを提供](https://docs.microsoft.com/visualstudio/extensibility/how-to-provide-context-for-editors)します。  
  
エディターのコンテキストは、エディターにフォーカスがあるか、ツール ウィンドウにフォーカスが移動された直前にフォーカスがあった場合にのみアクティブです。 次の手順に従って、エディターのコンテキストを行うことができます。  
  
1.  コンテキスト バッグを作成します。  
  
2.  選択範囲の要素の識別子 (SEID) コンテキスト バッグに発行します。  
  
3.  バッグ内のコンテキストを維持します。  
  
 これらのタスクは、次の手順で説明します。 コンテキストを提供する詳細については、次を参照してください。**堅牢なプログラミング**このトピックで後述します。  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>エディターまたはデザイナーのコンテキスト バッグを作成するには  
  
1.  呼び出す`QueryService`上、<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>のためのインターフェイス、<xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext>サービス。  
  
     ポインター、<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext>インターフェイスが返されます。  
  
2.  呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A>新しいコンテキストまたはサブコンテキストのバッグを作成します。  
  
     ポインター、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>インターフェイスが返されます。  
  
3.  呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>コンテキストまたはサブコンテキスト バッグに、属性、検索キーワード、または F1 キーワードを追加するメソッド。  
  
4.  サブコンテキスト バッグを作成する場合は、呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A>サブコンテキスト バッグを親のコンテキスト バッグにリンクするメソッド。  
  
5.  呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>通知を受信するときに、**ダイナミック ヘルプ**ウィンドウが更新しようとしています。  
  
     **ダイナミック ヘルプ**ウィンドウは、エディターを呼び出すコンテキストに変更する、更新が行われるまで遅延することができますを更新する準備ができ次第です。 これを行うと、時間のかかるアルゴリズムを実行しているシステムのアイドル時間が利用可能になるまで遅延できるため、パフォーマンスを向上できます。  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>コンテキスト バッグを SEID に発行するには  
  
1.  呼び出す`QueryService`上、<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>サービスへのポインターを返します、<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>インターフェイス。  
  
2.  呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>、要素の識別子を指定する (`elementid`パラメーター) をグローバル レベルにコンテキストを渡すことを示す SEID_UserContext の値。  
  
3.  内の値、ときに、エディターまたはデザイナーがアクティブになるその<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>オブジェクトは、グローバルの選択に反映されます。 セッションごとに 1 回は、このプロセスを完了し、作成すると、呼び出されたときにグローバル コンテキストへのポインターを格納するだけで済みます<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>します。  
  
### <a name="to-maintain-the-context-bag"></a>コンテキスト バッグを維持するには  
  
1.  実装<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>ことを確認する、**ダイナミック ヘルプ** ウィンドウの呼び出し、エディターまたはデザイナーの更新前にします。  
  
     各コンテキスト バッグと呼ばれる<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>コンテキスト バッグが作成され、インプリメント<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>、IDE 呼び出し<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>コンテキスト プロバイダー コンテキスト バッグが更新されることを通知します。 この呼び出しを使用して、属性とキーワード コンテキスト バッグ、および任意のサブコンテキスト バッグを変更する前に、**ダイナミック ヘルプ**ウィンドウの更新が発生します。  
  
2.  呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>エディターまたはデザイナーが新しいコンテキストを持つことを示すコンテキスト バッグにします。  
  
     ときに、**ダイナミック ヘルプ**ウィンドウ呼び出し<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>を示すこと、更新するときは、エディターまたはデザイナーは、その時点で、親のコンテキスト バッグと任意のサブコンテキスト バッグの両方を適切にコンテキストを更新できます。  
  
    > [!NOTE]
    >  `SetDirty`にフラグが設定されて自動的に`true`コンテキストが追加またはコンテキスト バッグから削除されるたびにします。 **ダイナミック ヘルプ** ウィンドウの呼び出しのみ<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>コンテキスト バッグの場合、`SetDirty`にフラグが設定されている`true`します。 リセットされます`false`更新後にします。  
  
3.  呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>アクティブ コンテキストのコレクションにコンテキストを追加または<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>コンテキストを削除します。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 独自のエディターを作成する場合は、エディターのコンテキストを提供するには、このトピックの手順の 3 つすべてを完了する必要があります。  
  
> [!NOTE]
>  呼び出す必要がある適切なエディターまたはデザイナー ウィンドウをアクティブにして、更新されるようにするコマンドのルーティングが正しく<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>フォーカス ウィンドウに、コンポーネントにします。  
  
 SEID は、変更の選択に基づくプロパティのコレクションです。 SEID 情報は、グローバルの選択を利用します。 によってトリガーされるイベントに、グローバルの選択がワイヤード (有線)、<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>インターフェイスであるすべての項目のリストを選択しています (現在のエディター、現在のツール ウィンドウ、現在の階層およびなど)。  
  
 エディターとデザイナー、たびにコンテキストを変更できますでカーソルが移動、単語内にあるコンテキスト バッグを常に更新する効率的ではありません。 効率的なエディターまたはデザイナー ウィンドウ内で移動カーソルを検出する任意の時点を更新するために、呼び出すことができます<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>します。 これまでのアイドル時間があるし、エディターまたはデザイナーに IDE のコンテキストのサービスが通知を送信してコンテキストの変更を保持することができます、**ダイナミック ヘルプ**ウィンドウを更新します。 このアプローチは、このトピックのコンテキスト バッグの管理"するには」の手順で使用されます。  
  
 後、エディターやデザイナー内のアクティビティのコンテキストを提供する、エディターまたはデザイナー自体のヘルプを表示するユーザーを許可する特定の F1 キーワードを指定する必要があります。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>

