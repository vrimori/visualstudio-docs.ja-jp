---
title: "方法: エディターのコンテキストの提供 |Microsoft ドキュメント"
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
caps.latest.revision: 17
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 362cd554e0723b1137d033440c9844d6cf3e59dd
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-provide-context-for-editors"></a>方法: エディターのコンテキストの提供
エディターのコンテキストは、エディターにフォーカスがあるか、ツール ウィンドウにフォーカスが移動された直前にフォーカスがあった場合にのみアクティブです。 次の手順に従って、エディターのコンテキストを指定できます。  
  
1.  コンテキスト バッグを作成します。  
  
2.  コンテキスト バッグを選択範囲の要素の識別子 (SEID) に発行します。  
  
3.  バッグにコンテキストを維持します。  
  
 次の手順では、これらのタスクについて説明します。 詳細については、コンテキストを提供する、次を参照してください。**堅牢なプログラミング**このトピックで後述します。  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>エディターまたはデザイナーのコンテキスト バッグを作成するには  
  
1.  呼び出す`QueryService`上、<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>のためのインターフェイス、<xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext>サービス</xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext></xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>。  
  
     ポインター、<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext>インターフェイスが返されます</xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext>。  
  
2.  呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A>新しいコンテキストまたはサブコンテキスト バッグを作成する方法</xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A>。  
  
     ポインター、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>インターフェイスが返されます</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>。  
  
3.  呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>コンテキストまたはサブコンテキスト バッグに、属性、検索キーワードまたは F1 キーワードを追加するメソッド</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>。  
  
4.  サブコンテキスト バッグを作成する場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A>サブコンテキスト バッグを親コンテキスト バッグにリンクする方法</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A>。  
  
5.  呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>通知を受信するときに、**ダイナミック ヘルプ**ウィンドウが更新されます</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>。  
  
     **ダイナミック ヘルプ**ウィンドウは、エディターを呼び出すコンテキストに変更する、更新が発生するまで遅延することができるように更新する準備がある場合。 これを行うと、時間のかかるアルゴリズムを実行しているシステムのアイドル時間が利用可能になるまでの遅延を許容するためにパフォーマンスを向上できます。  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>コンテキスト バッグを SEID に発行するには  
  
1.  呼び出す`QueryService`上、<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>サービスへのポインターを返す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>インターフェイス</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx></xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>。  
  
2.  呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>、要素の識別子を指定する (`elementid`パラメーター)、グローバル レベルにコンテキストを渡すことを示すために SEID_UserContext の値</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>。  
  
3.  内の値がエディターやデザイナーのアクティブ、<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>オブジェクトは、グローバルな選択状態に反映されます</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>。 セッションごとに&1; 回、このプロセスを完了し、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>。</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>が呼び出されたときに作成されたグローバル コンテキストへのポインターを格納するだけで  
  
### <a name="to-maintain-the-context-bag"></a>コンテキスト バッグを維持するために  
  
1.  実装<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>いることを確認する、**ダイナミック ヘルプ** ウィンドウの呼び出しエディターまたはデザイナーの更新前に</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>。  
  
     呼び出したコンテキスト バッグの<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>コンテキスト バッグが作成され、インプリメント<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>、IDE 呼び出し<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>コンテキスト バッグに更新するコンテキストのプロバイダーに通知する</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>。 この呼び出しを使用して、属性とキーワード コンテキスト バッグでは、サブコンテキスト バッグ内の前に変更することができます、**ダイナミック ヘルプ**ウィンドウの更新が発生します。  
  
2.  呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>エディターまたはデザイナーが新しいコンテキストを持つことを示すためにコンテキスト バッグの</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>。  
  
     ときに、**ダイナミック ヘルプ**ウィンドウ呼び出し<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>を示すことに更新される、エディターまたはデザイナーは、その時点で親コンテキスト バッグと任意のサブコンテキスト バッグの両方の適切なコンテキストを更新できます</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>。  
  
    > [!NOTE]
    >  `SetDirty`にフラグが自動的に設定`true`するたびにコンテキストが追加またはコンテキスト バッグから削除します。 **ダイナミック ヘルプ** ウィンドウの呼び出しのみ<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>コンテキスト バッグの場合、`SetDirty`にフラグが設定されている`true`</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>。 リセットされます`false`の更新の後です。  
  
3.  呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>アクティブ コンテキストのコレクションにコンテキストを追加するか、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>コンテキストを削除する</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 独自のエディターを作成する場合は、エディターのコンテキストを提供するには、このトピックの手順の&3; つすべてを完了する必要があります。  
  
> [!NOTE]
>  適切なエディターまたはデザイナー ウィンドウをアクティブにして、更新されるようにするコマンドのルーティングが正常に呼び出す必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>フォーカス ウィンドウを作成するコンポーネント</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>。  
  
 SEID は、選択内容に基づいて変更するプロパティのコレクションです。 SEID 情報は、グローバルな選択状態で利用できます。 によってトリガーされるイベントにグローバルな選択状態がワイヤード (有線)、<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>インターフェイス、およびすべての項目の一覧が選択されています (現在のエディター、現在のツール ウィンドウ、現在の階層およびなど).</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>  
  
 エディターとデザイナーでのコンテキストとなるをするたびに変更することができます、カーソルが移動、word 内でコンテキスト バッグを絶えず更新効率的ではありません。 効率的なエディターまたはデザイナー ウィンドウ内での移動のカーソルを検出する任意の時間を更新するために、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>を呼び出すことができます。 これを使用すると、アイドル時間があるし、エディターまたはデザイナーを IDE のコンテキストのサービスが通知を送信するまで、コンテキストの変更内容を保持、**ダイナミック ヘルプ**ウィンドウを更新します。 このトピックのコンテキスト バッグの管理"するには」の手順では、このアプローチを使用します。  
  
 エディターまたはデザイナー内のアクティビティ コンテキストを指定した後は、エディターまたはデザイナー自体のヘルプを表示するユーザーを許可するように、特定の F1 キーワードを入力してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx></xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>
