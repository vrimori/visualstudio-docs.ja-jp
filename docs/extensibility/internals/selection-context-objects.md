---
title: "コンテキスト オブジェクトの選択 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
caps.latest.revision: 13
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
ms.openlocfilehash: 3fa5093ee38c364a4766160f8642755bc0b2a23f
ms.lasthandoff: 02/22/2017

---
# <a name="selection-context-objects"></a>コンテキスト オブジェクトの選択
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) は選択範囲のグローバル コンテキスト オブジェクトを使用して IDE で表示される内容が決まります。 IDE では、各期間では、グローバルの選択コンテキストにプッシュされた独自の選択コンテキスト オブジェクトをあることができます。 IDE は、そのウィンドウにフォーカスがあるウィンドウから値を持つグローバル選択コンテキストを更新します。 詳細については、次を参照してください。[をユーザーにフィードバック](../../extensibility/internals/feedback-to-the-user.md)します。  
  
 ウィンドウ フレームまたは IDE でのサイトはそれぞれが<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>。</xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>と呼ばれるサービス ウィンドウ フレームに配置された、VSPackage によって作成されたオブジェクトを呼び出す必要があります、`QueryService`へのポインターを取得するメソッド、<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>インターフェイス</xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>。  
  
 フレーム ウィンドウには、それらの選択コンテキスト情報は、起動されたときにグローバル選択コンテキストに反映されない部分を保持できます。 この機能は、空の選択範囲で開始する可能性のあるツール ウィンドウに便利です。  
  
 Vspackage を監視できるグローバルの選択コンテキスト トリガー イベントを変更します。 VSPackages が実装することで、次のタスクを実行できます`IVsTrackSelectionEx`と<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>インターフェイス:</xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>  
  
-   階層内の現在アクティブなファイルを更新します。  
  
-   特定の種類の要素への変更を監視します。 VSPackage を使用する特別な場合など**プロパティ**ウィンドウで、アクティブな変更を監視する**プロパティ**ウィンドウし必要な場合に自分を再起動します。  
  
 次の順序は、追跡の選択範囲の一般的な手順を示しています。  
  
1.  IDE では、新しく開かれたウィンドウから選択コンテキストを取得し、グローバル選択コンテキストに配置します。 HIERARCHY_DONTPROPAGATE または SELCONTAINER_DONTPROPAGATE を選択コンテキストを使用する場合、グローバル コンテキストにその情報は反映されません。 詳細については、次を参照してください。[をユーザーにフィードバック](../../extensibility/internals/feedback-to-the-user.md)します。  
  
2.  通知イベントは、それらを要求したすべての VSPackage にブロードキャストされます。  
  
3.  VSPackage では、ツール、またはその他の同様のタスクを再アクティブ化し、階層の更新などのアクティビティを実行することによって受信イベントに対して動作します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection></xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>   
 [Visual Studio での階層](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [選択と、IDE 内の通貨](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [プロジェクトの種類](../../extensibility/internals/project-types.md)
