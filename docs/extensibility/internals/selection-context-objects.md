---
title: コンテキスト オブジェクトの選択 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 04ccc4a57ac7af144c134761119433b7533e9bec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="selection-context-objects"></a>コンテキスト オブジェクトの選択
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) では、グローバルの選択コンテキスト オブジェクトを使用して、IDE で何を表示するかを判断します。 IDE では、各ウィンドウは、グローバルの選択コンテキストにプッシュされた独自の選択コンテキスト オブジェクトができます。 IDE は、そのウィンドウにフォーカスがあるときにウィンドウから値を持つグローバルの選択コンテキストを更新します。 詳細については、次を参照してください。[をユーザーにフィードバック](../../extensibility/internals/feedback-to-the-user.md)です。  
  
 ウィンドウ フレームまたは IDE でのサイトはそれぞれが呼び出されるサービス<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>です。 ウィンドウ フレームのコンテナーに配置されている VSPackage によって作成されたオブジェクトを呼び出す必要があります、`QueryService`へのポインターを取得するメソッド、<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>インターフェイスです。  
  
 フレーム ウィンドウには、その選択コンテキスト情報は、起動されたときに、グローバルの選択コンテキストに反映されないの部分を保持できます。 この機能は、空の選択範囲で開始する可能性のあるツール ウィンドウに便利です。  
  
 Vspackage が監視できるグローバルの選択コンテキスト トリガー イベントを変更します。 Vspackage が実装することで、次のタスクを実行できます`IVsTrackSelectionEx`と<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>インターフェイス。  
  
-   階層内の現在アクティブなファイルを更新します。  
  
-   モニターは、特定の要素型に変更します。 例では、VSPackage は、特殊なを使用している場合の**プロパティ**ウィンドウで、アクティブに変更を監視できます**プロパティ**ウィンドウ再起動に必要なときに自分のものとします。  
  
 次の順序は、選択の追跡の一般的な一連の措置を示します。  
  
1.  IDE では、新しく開かれたウィンドウから選択コンテキストを取得し、グローバルの選択コンテキストに配置します。 HIERARCHY_DONTPROPAGATE または SELCONTAINER_DONTPROPAGATE 選択コンテキストを使用する場合、その情報は、グローバルなコンテキストには反映されません。 詳細については、次を参照してください。[をユーザーにフィードバック](../../extensibility/internals/feedback-to-the-user.md)です。  
  
2.  通知イベントは、それらを要求する任意の VSPackage にブロードキャストされます。  
  
3.  VSPackage は、ツール、またはその他の同様のタスクを再アクティブ化して、階層の更新などのアクティビティを実行することによって受信イベントに対して動作します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>   
 [Visual Studio での階層](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [選択範囲と、IDE の通貨](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [プロジェクト タイプ](../../extensibility/internals/project-types.md)