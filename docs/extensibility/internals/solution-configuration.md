---
title: ソリューションの構成 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ec88e383c7ad0a74699f984691d337da7d6a2cac
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53835034"
---
# <a name="solution-configuration"></a>ソリューション構成
ソリューション構成では、ソリューション レベルのプロパティを格納します。 動作を指示する、**開始**(F5) キーと**ビルド**コマンド。 既定では、これらのコマンドは、ビルドし、デバッグ構成を開始します。 どちらのコマンドは、ソリューション構成のコンテキストで実行します。 これは、ユーザーがどのようなアクティブなソリューションが、設定を使用して構成されているビルドの開始、f5 キーを予測できることを意味します。 環境は、ビルドおよび実行する際にプロジェクトではなく、ソリューションを最適化するために設計されています。  
  
 標準の Visual Studio ツールバーには、[スタート] ボタンとソリューション構成ドロップダウンを [スタート] ボタンの右側が含まれています。 この一覧では、f5 キーが押されたときに開始する構成を選択して、独自のソリューション構成を作成または既存の構成を編集することができます。  
  
> [!NOTE]
>  機能拡張インターフェイスを作成またはソリューション構成を編集することはありません。 使用する必要があります`DTE.SolutionBuilder`します。 ただし、ソリューションのビルドを管理するの拡張性 Api があります。 詳細については、「 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2> 」を参照してください。  
  
 次に、プロジェクトの種類でサポートされるソリューション構成を実装する方法を示します。  
  
- プロジェクト  
  
   現在のソリューションに存在するプロジェクトの名前が表示されます。  
  
- 構成  
  
   プロジェクトの種類でサポートされる構成の一覧を提供し、実装、プロパティ ページに表示される<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>します。  
  
   構成 列では、このソリューション構成でビルドするプロジェクト構成の名前を表示し、矢印ボタンをクリックすると、すべてのプロジェクト構成ファイルを一覧表示されます。 環境は、<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A>メソッドがこの一覧に入力します。 場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A>メソッドを示すことをサポートするプロジェクト構成の編集、新規または編集の選択は構成という見出しの下も表示されます。 これらの各選択のメソッドを呼び出すためのダイアログ ボックスを起動、`IVsCfgProvider2`プロジェクトの構成を編集するインターフェイス。  
  
   プロジェクトが構成をサポートしていない場合、構成 列は None が表示されは無効です。  
  
- プラットフォーム  
  
   選択したプロジェクトの構成、ビルドで、矢印ボタンをクリックするとすべてのプロジェクトで使用可能なプラットフォームの一覧表示されます。 プラットフォームが表示されます。 環境は、<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A>メソッドがこの一覧に入力します。 場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A>メソッドを示します、プロジェクトをサポートするプラットフォームの編集、新規にも、プラットフォームという見出しの下の編集の選択内容が表示されます。 これらの各選択の起動 ダイアログ ボックスを呼び出す`IVsCfgProvider2`プロジェクトの使用可能なプラットフォームを編集する方法。  
  
   プロジェクトがプラットフォームをサポートしていない場合、そのプロジェクトのプラットフォームの列は None が表示されは無効です。  
  
- ビルド  
  
   現在のソリューション構成でプロジェクトをビルドするかどうかを指定します。 プロジェクトの依存関係が含まれているにもかかわらず、ソリューション レベルのビルド コマンドを呼び出すときに、選択されていないプロジェクトはビルドされません。 プロジェクトをビルドするのには選択されていないはまだデバッグ、実行、パッケージ化、およびソリューションの展開に含まれます。  
  
- デプロイ  
  
   選択したソリューションのビルド構成とスタートまたは Deploy コマンドを使う場合にプロジェクトを配置するかどうかを指定します。 このフィールドのチェック ボックスを使用できるは、プロジェクトは、実装することによって展開をサポートしている場合になります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>インターフェイスをその<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>オブジェクト。  
  
  新しいソリューション構成を追加すると、ユーザーから選択できますソリューション構成のドロップダウン リスト ボックス、標準ツールバーをビルドしたり、その構成を開始します。  
  
## <a name="see-also"></a>関連項目  
 [構成オプションの管理](../../extensibility/internals/managing-configuration-options.md)   
 [ビルドするためのプロジェクト構成](../../extensibility/internals/project-configuration-for-building.md)   
 [プロジェクト構成オブジェクト](../../extensibility/internals/project-configuration-object.md)