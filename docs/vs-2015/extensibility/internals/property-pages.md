---
title: プロパティ ページ |Microsoft Docs
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
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 544f69a8cfa90c7977a2861452fa47a570eb0bbb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539622"
---
# <a name="property-pages"></a>プロパティ ページ
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[プロパティ ページ](https://docs.microsoft.com/visualstudio/extensibility/internals/property-pages)します。  
  
ユーザーは、表示し、プロパティ ページを使用して、プロジェクトの構成に依存して、独立系のプロパティを変更できます。 A**プロパティ ページ**でボタンが有効になっている、**プロパティ**ウィンドウまたはソリューション エクスプ ローラー ツールバーの選択したオブジェクトのプロパティ ページのビューを提供するオブジェクト。 プロパティ ページでは、環境によって作成され、ソリューションとプロジェクトの利用します。 することができます、ただし、使用可能にするプロジェクト項目が構成依存のプロパティを使用します。 プロジェクト内のファイルを正しくビルドする別のコンパイラ スイッチの設定を必要とする場合は、この機能を使用する可能性があります。  
  
## <a name="using-property-pages"></a>プロパティ ページの使用  
 プロパティ ページがまだ表示されている (たとえば、プロジェクトをソリューション) から選択が変更された場合は、情報のページで、新しい選択範囲のプロパティを表示する変更表示されます。 プロパティ ページをサポートするオブジェクトのプロパティがない場合は、プロパティ ページが空です。  
  
 複数のオブジェクトが選択されている場合、プロパティ ページには、選択したすべてのアイテムのプロパティの積集合が表示されます。 選択した項目に構成に依存するプロパティが含まれていないかどうか、**プロパティ ページ**ソリューション エクスプ ローラー ツールバーのボタンがクリックされると、[プロパティ] ウィンドウにフォーカスが変更されます。 [プロパティ] ウィンドウと選択範囲に関連する詳細については、次を参照してください。[拡張プロパティ](../../extensibility/internals/extending-properties.md)します。  
  
 複数のオブジェクトのプロパティが表示されますが、[プロパティ] ページの値を変更して場合、が最初に異なると、個々 のオブジェクトのプロパティが表示されていたときに、ページが空白場合でも、新しい値に設定のすべてのオブジェクトの値は。  
  
 2 つの一般的な種類があります**ProjectProperty ページ** ダイアログ ボックスで使用できる[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。 Visual Basic プロジェクトの場合、最初になど、プロパティ ページは表示フィールドの形式を使用して次のスクリーン ショットに示すようにします。 1 秒間、後でこのセクションで示す、プロパティ ページのホスト プロパティ グリッド プロパティ ウィンドウに似ています。  
  
 ![Visual Basic プロパティ ページ](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages")  
フィールドの形式とツリー構造を持つプロジェクト プロパティ ページ ダイアログ ボックス  
  
 プロパティ ページ ダイアログ ボックスのツリー構造を使用して組み込まれていない<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>します。 によって渡されたレベル名に基づいて、環境、<xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>インターフェイスは、それを構築します。  
  
 使用できる 2 つの最上位のカテゴリは[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]プロパティ ページ。  
  
-   一般的なプロパティは、選択したオブジェクトまたはオブジェクトの構成に依存しない情報が表示されます。 その結果、一般的なプロパティのサブカテゴリのいずれかを選択した場合、構成、プラットフォーム、および Configuration Manager のオプション ダイアログ ボックスの上部には使用できません。  
  
-   ソリューションまたはプロジェクトのデバッグ、最適化、およびビルドのパラメーターに関連する構成に依存する情報を含む構成のプロパティ。  
  
 その他の最上位のカテゴリを作成することはできませんの実装のどちらか一方を表示しないように選択できます`IVsPropertyPage`します。 たとえば、オブジェクトを表示するには、任意の構成に依存しないプロパティがない場合、一般的なプロパティのカテゴリを表示しないようにすることもできます。 場合、一般的なプロパティを表示する`ISpecifyPropertyPages`を実装するときに、項目の参照オブジェクトと構成のプロパティから実装`ISpecifyPropertyPages`構成オブジェクト (実装するオブジェクト`IVsCfg`、 `IVsProjectCfg`、および関連します。インターフェイスの場合)。  
  
 最上位のカテゴリの下に表示される各カテゴリは、個別のプロパティ ページを表します。 Category と subcategory 使用できるエントリ ダイアログ ボックスでは、実装によって決まります`ISpecifyPropertyPages`と`IVsPropertyPage`します。  
  
 `IDispatch` オブジェクトのプロパティ ページの実装に表示されるプロパティを持つ選択コンテナー内のアイテム`ISpecifyPropertyPages`クラス Id の一覧を列挙します。 クラス Id が変数として渡される`ISpecifyPropertyPages`プロパティ ページをインスタンス化に使用されます。 クラス Id の一覧に渡されます`IVsPropertyPage` ダイアログ ボックスの左側のツリー構造を作成します。 プロパティ ページ、パス情報を`IDispatch`を実装するオブジェクト`ISpecifyPropertyPages`が各ページの情報を入力するとします。  
  
 参照オブジェクトのプロパティを使用して取得`IDispatch`選択コンテナー内の各オブジェクト。  
  
 実装する`Help::DisplayTopicFromF1Keyword`VSPackage で、[ヘルプ] ボタンの機能を提供します。  
  
 詳細については、次を参照してください。`IDispatch`と`ISpecifyPropertyPages`、MSDN ライブラリ。  
  
 プロパティ ページの 2 つ目の種類が表示されますサンプル ホストで、プロパティ グリッドのフォームに次のスクリーン ショットで示すよう。  
  
 ![VC プロパティ ページ](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages")  
プロパティ グリッドでプロパティ ページ ダイアログ ボックス  
  
 インターフェイス`IVSMDPropertyBrowser`と`IVSMDPropertyGrid`(vsmanaged.h で宣言) を作成し、ダイアログ ボックスまたはウィンドウ内のプロパティ グリッドを設定するために使用します。  
  
 プロジェクトのアーキテクチャが大幅に変わったの過去のバージョンから[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。 具体的には、プロジェクトの概念がアクティブに変更します。 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]、アクティブなプロジェクトの概念はありません。 前の開発環境では、アクティブなプロジェクトは、プロジェクトをビルドおよび配置のコマンドは、コンテキストに関係なくに既定値はでした。 ソリューションの制御し、調停ビルド コマンドおよび deploy コマンドを次に、どのプロジェクトに適用されます。  
  
 アクティブなプロジェクトいたは 3 つの方法のいずれかでキャプチャされたようになりました。  
  
-   スタートアップ プロジェクト  
  
     ユーザーは、f5 キーを押すか、ビルド メニューから実行を選択するときに開始されるソリューションのプロパティ ページからプロジェクトを指定できます。 これは、ソリューション エクスプ ローラーで太字のフォントでその名前が表示されることの意味では、古いアクティブなプロジェクトと同様の方法で機能します。  
  
     オートメーション モデルのプロパティとしてスタートアップ プロジェクトを取得するには呼び出すことによって`DTE.Solution.SolutionBuild.StartupProjects`します。 呼び出すことで、VSPackage、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A>または<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A>メソッド。 `IVsSolutionBuildManager` サービスとして利用できます`QueryService`SID_SVsSolutionBuildManager にします。 詳細については、次を参照してください。[プロジェクト構成オブジェクト](../../extensibility/internals/project-configuration-object.md)と[ソリューション構成](../../extensibility/internals/solution-configuration.md)します。  
  
-   アクティブなソリューションのビルド構成  
  
     [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] アクティブ ソリューション構成を実装して、オートメーション モデルで使用できるは`DTE.Solution.SolutionBuild.ActiveConfiguration`します。 ソリューション構成では、(各プロジェクトは複数の構成を異なる名前で、複数のプラットフォーム上に持つことができます)、ソリューション内の各プロジェクトの 1 つのプロジェクト構成を含むコレクションです。 ソリューションのプロパティ ページに関連する詳細については、次を参照してください。[ソリューション構成](../../extensibility/internals/solution-configuration.md)します。  
  
-   現在選択されているプロジェクト  
  
     実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A>プロジェクト階層し、プロジェクト項目または選択した項目を取得します。 DTE から使用すると、`SelectedItems.SelectedItem.Project`と`SelectedItems.SelectedItem.ProjectItem`メソッド。 コアでこれらの見出しの下のサンプル コードがある[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]ドキュメント。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>   
 [構成オプションの管理](../../extensibility/internals/managing-configuration-options.md)   
 [プロジェクト構成オブジェクト](../../extensibility/internals/project-configuration-object.md)   
 [ソリューション構成](../../extensibility/internals/solution-configuration.md)

