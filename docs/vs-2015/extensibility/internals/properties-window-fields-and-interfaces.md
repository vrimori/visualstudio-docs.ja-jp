---
title: Properties Window Fields and インターフェイス |Microsoft Docs
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
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3aa3daa8925c9fec79f80d4d2fa6b4e8365b15b2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49929336"
---
# <a name="properties-window-fields-and-interfaces"></a>プロパティ ウィンドウのフィールドとインターフェイス
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

モデルの選択で表示される情報を決定する、**プロパティ**ウィンドウは IDE でフォーカスのあるウィンドウに基づきます。 すべてのウィンドウと、選択したウィンドウ内のオブジェクトには、その選択コンテキスト オブジェクトのグローバルの選択コンテキストにプッシュされることができます。 環境は、そのウィンドウにフォーカスがあるときに、ウィンドウ フレームの値でグローバルの選択コンテキストを更新します。 フォーカスが変更されたときにも選択コンテキスト。  
  
## <a name="tracking-selection-in-the-ide"></a>IDE での選択の追跡  
 ウィンドウ フレームまたは、IDE によって所有されているサイトと呼ばれるサービスを持つ<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>します。 もう 1 つ開いているウィンドウにフォーカスを変更するか、内の別のプロジェクト項目を選択すると、ユーザーが原因と、選択した方法を変更に、次の手順が表示**ソリューション エクスプ ローラー**、に表示される内容を変更するのには**プロパティ**ウィンドウ。  
  
1. 選択したウィンドウの呼び出しでは配置されている VSPackage によって作成されたオブジェクト<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>が<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>します。  
  
2. 選択したウィンドウ、によって提供される、選択コンテナーを作成、独自<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>オブジェクト。 呼び出すときに、選択内容、VSPackage<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>環境では、すべてのリスナーに通知するなど、**プロパティ**ウィンドウで、変更します。 新しい選択範囲に関連する階層と項目の情報へのアクセスも提供します。  
  
3. 呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>で選択した階層アイテムを渡すと、`VSHPROPID_BrowseObject`パラメーターは設定します、<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>オブジェクト。  
  
4. 派生したオブジェクト、 [IDispatch インターフェイス](http://msdn.microsoft.com/en-us/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)に対して返される<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>、項目は、次の要求、および環境にラップします、 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (次の手順を参照してください)。 環境は、2 番目の呼び出しの呼び出しが失敗した場合、 `IVsHierarchy::GetProperty`、選択コンテナーを渡す<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>階層アイテムまたはアイテムを指定します。  
  
    VSPackage を作成できませんが、プロジェクト<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>を実装する VSPackage に、環境が指定したウィンドウのため (たとえば、**ソリューション エクスプ ローラー**) を構築します<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>の代わりに。  
  
5. 環境のメソッドを呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>に基づいてオブジェクトを取得、`IDispatch`インターフェイスを埋めるために、**プロパティ**ウィンドウ。  
  
   内の値、**プロパティ**ウィンドウが変更には、Vspackage 実装`IVsTrackSelectionEx::OnElementValueChangeEx`と`IVsTrackSelectionEx::OnSelectionChangeEx`要素の値に変更を報告します。 環境が呼び出され、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>または<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>に表示される情報を保持する、**プロパティ**ウィンドウは、プロパティの値と同期します。 詳細については、次を参照してください。[プロパティ ウィンドウでプロパティ値を更新](../../misc/updating-property-values-in-the-properties-window.md)します。  
  
   別の選択をするだけでなくプロジェクト項目で**ソリューション エクスプ ローラー**その項目に関連するプロパティを表示するで使用可能なドロップダウン リストを使用して、フォームまたはドキュメント ウィンドウ内から別のオブジェクトも選択できます、**プロパティ**ウィンドウ。 詳細については、次を参照してください。[プロパティ ウィンドウのオブジェクト一覧](../../extensibility/internals/properties-window-object-list.md)します。  
  
   情報の表示方法を変更することができます、**プロパティ**からアルファベット順をカテゴリ別のウィンドウのグリッドまた、、で適切なボタンをクリックして、選択したオブジェクトのプロパティページを開くことも、使用可能な場合。**プロパティ**ウィンドウ。 詳細については、次を参照してください。[プロパティ ウィンドウのボタン](../../extensibility/internals/properties-window-buttons.md)と[プロパティ ページ](../../extensibility/internals/property-pages.md)します。  
  
   最後に、下部にある、**プロパティ**ウィンドウで選択したフィールドの説明も含まれています、**プロパティ** ウィンドウのグリッド。 詳細については、次を参照してください。[プロパティ ウィンドウからフィールドの説明を取得する](../../misc/getting-field-descriptions-from-the-properties-window.md)します。  
  
## <a name="see-also"></a>関連項目  
 [プロパティの拡張](../../extensibility/internals/extending-properties.md)

