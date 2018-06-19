---
title: ソリューションの構成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f7b2a453d4ea4e8b92b40ee126f9441e6f353606
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132722"
---
# <a name="solution-configuration"></a>ソリューション構成
ソリューション構成では、ソリューション レベルのプロパティを格納します。 動作を指示する、**開始**(F5) キーと**ビルド**コマンド。 既定では、これらのコマンドは、ビルドし、デバッグ構成を開始します。 どちらのコマンドは、ソリューション構成のコンテキストで実行します。 これは、ユーザーがどのようなアクティブなソリューションが、設定で構成されているビルドの開始、f5 キーを予測できることを意味します。 環境が構築および実行する際に、プロジェクトではなく、ソリューションを最適化するために設計されています。  
  
 標準の Visual Studio ツールバーには、[スタート] ボタンとドロップダウンを [スタート] ボタンの右側に使用するソリューション構成が含まれています。 この一覧では、f5 キーが押されたときに起動する構成を選択して、独自のソリューション構成を作成または既存の構成を編集することができます。  
  
> [!NOTE]
>  機能拡張インターフェイスを作成またはソリューション構成を編集することはありません。 使用する必要があります`DTE.SolutionBuilder`です。 ただし、ソリューションのビルドを管理するためが機能拡張 Api があります。 詳細については、「<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>」を参照してください。  
  
 次に、プロジェクトの種類でサポートされているソリューションの構成を実装する方法を示します。  
  
-   プロジェクト  
  
     現在のソリューションに存在するプロジェクトの名前を表示します。  
  
-   構成  
  
     プロジェクトの種類でサポートされている構成の一覧を指定して、実装プロパティ ページに表示する<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>です。  
  
     構成 列では、このソリューション構成でビルドするプロジェクト構成の名前を表示し、矢印ボタンをクリックするとすべてのプロジェクト構成の一覧を表示します。 環境の呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A>メソッドがこの一覧を入力します。 場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A>メソッドか、サポートするプロジェクト構成の編集、新しい、またはかも、構成という見出しの下のオプションの編集が表示されます。 これらの各選択のメソッドを呼び出す ダイアログ ボックスを起動して、`IVsCfgProvider2`プロジェクトの構成を編集するインターフェイスです。  
  
     プロジェクトが構成をサポートしていない場合、構成 列は なし が表示されは無効になります。  
  
-   プラットフォーム  
  
     選択したプロジェクト構成は、ビルドされ、矢印ボタンをクリックするとすべてのプロジェクトで使用可能なプラットフォームの一覧を表示、プラットフォームが表示されます。 環境の呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A>メソッドがこの一覧を入力します。 場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A>メソッドか、プロジェクトをサポートしているプラットフォームの編集、新しい、またはかも、プラットフォームという見出しの下のオプションの編集が表示されます。 呼び出すためのダイアログ ボックスを起動してこれらの各選択`IVsCfgProvider2`プロジェクトの使用可能なプラットフォームを編集する方法です。  
  
     プロジェクトがプラットフォームをサポートしていない場合、そのプロジェクトのプラットフォームの列は None が表示されは無効になります。  
  
-   ビルド  
  
     現在のソリューション構成でプロジェクトをビルドするかどうかを指定します。 ソリューション レベルのビルド コマンドが含まれているプロジェクトの依存関係にかかわらず呼び出されたときに選択されていないプロジェクトが構築されていません。 プロジェクトをビルドするのには選択されていないはまだデバッグ、実行、パッケージ、およびソリューションの展開に含まれます。  
  
-   配置  
  
     選択したソリューションのビルド構成で起動または配置コマンドを使用する場合に、プロジェクトを配置するかどうかを指定します。 このフィールドのチェック ボックス、プロジェクトは、実装することで展開をサポートしている場合は利用できなくなります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>インターフェイスをその<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>オブジェクト。  
  
 新しいソリューション構成が追加されると、ユーザーを選択できますが、ソリューション構成がドロップダウン リスト ボックスから [標準] ツールバーを構築したり、その構成を開始したりします。  
  
## <a name="see-also"></a>関連項目  
 [構成オプションの管理](../../extensibility/internals/managing-configuration-options.md)   
 [構築するためのプロジェクトの構成](../../extensibility/internals/project-configuration-for-building.md)   
 [プロジェクト構成オブジェクト](../../extensibility/internals/project-configuration-object.md)