---
title: カスタム プロジェクトと項目テンプレートの作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fc866c9a0cd5f3aaaa06e5bc59ea2427cc86268a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="creating-custom-project-and-item-templates"></a>カスタム プロジェクトと項目テンプレートを作成します。

Visual Studio SDK には、カスタム プロジェクト テンプレートとカスタム項目テンプレートを作成するプロジェクト テンプレートが含まれています。 これらのテンプレートは、いくつか共通パラメーターの代用を含めるし、zip ファイルとしてビルドします。 これらは自動的に配置していないは実験用インスタンスで使用できません。 ユーザー テンプレート ディレクトリに生成された zip ファイルをコピーする必要があります。
  
テンプレートの作成テンプレートを使用してより大きな拡張機能でテンプレートを追加できます。 これにより、ソース ファイルでのバージョン管理を実装し、1 つの VSIX パッケージ プロジェクト テンプレートのグループを作成できます。  
  
NuGet パッケージをインストールするためのテンプレートを構成することもできます。 詳細については、次を参照してください。 [Visual Studio のテンプレートで NuGet パッケージ](/nuget/visual-studio-extensibility/visual-studio-templates)です。

基本的なテンプレートの作成シナリオで使用する必要があります、**テンプレートのエクスポート**ウィザードで、圧縮されたファイルに出力します。 基本的なテンプレートの作成の詳細については、次を参照してください。[を作成するプロジェクトと項目テンプレート](../ide/creating-project-and-item-templates.md)です。  

> [!NOTE]
> Visual Studio 2017 以降、カスタム プロジェクトと項目テンプレートのスキャンが不要になった実行されます。 代わりに、拡張機能では、これらのテンプレートのインストール場所を記述するテンプレート マニフェスト ファイルを提供する必要があります。 Visual Studio 2017 を使用するには、VSIX 拡張機能を更新します。 MSI を使用して、拡張機能を展開する場合は、テンプレート マニフェスト ファイルを手動で生成する必要があります。 詳細については、次を参照してください。[をアップグレードするカスタムのプロジェクトと項目テンプレート Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md)です。 テンプレート マニフェスト スキーマについては、「 [Visual Studio テンプレート マニフェスト スキーマ リファレンス](../extensibility/visual-studio-template-manifest-schema-reference.md)です。

## <a name="creating-a-project-template"></a>プロジェクト テンプレートの作成  
  
1.  プロジェクト テンプレート プロジェクトを作成します。 プロジェクト テンプレートを見つけることができます、**新しいプロジェクト** ダイアログ ボックスで、Visual Basic または Visual c# **Extensibility**フォルダーです。  
  
     テンプレートは、クラス ファイル、アイコン、.vstemplate ファイル、名前付き ProjectTemplate.vbproj または ProjectTemplate.csproj、編集可能なプロジェクト ファイル、およびその他のプロジェクトの種類によって、このような resources.resx ファイル、AssemblyInfo 通常生成されるいくつかのファイルが生成されます。ファイル、および .settings ファイル。 各コード ファイルには、適切な場所の一般的なパラメーターの代用が含まれています。  
  
2.  追加し、プロジェクトの必要に応じてプロジェクトから項目を削除します。 編集可能なプロジェクト ファイル、AssemblyInfo ファイルまたは .vstemplate ファイルを削除しないでください。  
  
3.  任意の追加と削除を反映するように、.vstemplate ファイルを更新します。 [プロジェクト](../extensibility/project-element-visual-studio-templates.md)要素を含める必要があります、 [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)テンプレートに含まれる各ファイルの要素。  
  
4.  コード ファイルおよびその他のユーザー向けのコンテンツを変更し、適切なパラメーターの代用を追加します。  
  
5.  必要に応じて生成されるコンテンツを変更します。  
  
6.  プロジェクトをビルドします。  
  
     Visual Studio では、テンプレートが含まれている .zip ファイルを作成します。 展開されていないは実験用インスタンスで使用できません。  
  
## <a name="creating-an-item-template"></a>項目テンプレートを作成します。  
  
1.  項目テンプレート プロジェクトを作成します。  
  
     テンプレートは、クラス ファイル、アイコン、.vstemplate ファイル、および AssemblyInfo ファイルを生成します。 クラス ファイルには、共通パラメーターの代用が含まれています。  
  
2.  追加し、プロジェクトの必要に応じてプロジェクトから項目を削除します。  
  
3.  任意の追加と削除を反映するように、.vstemplate ファイルを更新します。 [プロジェクト](../extensibility/project-element-visual-studio-templates.md)要素を含める必要があります、 [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)テンプレートに含まれる各ファイルの要素。  
  
4.  コード ファイルおよびその他のユーザー向けのコンテンツを変更し、適切なパラメーターの代用を追加します。  
  
5.  必要に応じて生成されるコンテンツを変更します。  
  
6.  プロジェクトをビルドします。  
  
     Visual Studio では、テンプレートが含まれている圧縮ファイルを作成します。 展開されていないは実験用インスタンスで使用できません。  
  
## <a name="deployment"></a>配置  
  
#### <a name="to-deploy-the-project-or-item-template"></a>プロジェクトまたは項目テンプレートをデプロイするには  
  
1.  VSIX プロジェクトを作成する。 詳細については、次を参照してください。 [VSIX プロジェクト テンプレート](../extensibility/vsix-project-template.md)です。  
  
2.  VSIX プロジェクトをスタートアップ プロジェクトとして設定します。 **ソリューション エクスプ ローラー**、選択、VSIX プロジェクト ノードを右クリックし、**スタートアップ プロジェクトとして設定**です。  
  
3.  プロジェクト テンプレートを VSIX プロジェクトのアセットとして設定します。 .Vsixmanifest ファイルを開きます。 移動して、**資産** タブでをクリックし、**新規**です。  
  
    1.  設定、**型**フィールドを**[microsoft.visualstudio.projecttemplate]**または**[microsoft.visualstudio.itemtemplate]**です。  
  
    2.  ソースの選択、**現在のソリューション内のプロジェクト**オプション、およびテンプレートが含まれているプロジェクトを選択します。  
  
4.  ソリューションをビルドし、F5 キーを押します。 実験用インスタンスが表示されます。  
  
5.  プロジェクト テンプレート プロジェクトの場合に表示されているプロジェクト テンプレートが表示されます、**新しいプロジェクト**ダイアログ (**ファイル > 新規 > プロジェクト**) では、Visual c# または Visual Basic のノードです。 項目テンプレート プロジェクトでは、項目テンプレートが 新しい項目の追加 ダイアログ ボックスの一覧に表示されます (で、**ソリューション エクスプ ローラー**プロジェクト ノードを選択して、をクリックして**追加/新しい項目の**)。  
  
## <a name="see-also"></a>関連項目

[Visual Studio テンプレート参照](../ide/visual-studio-template-reference.md)  
[Visual Studio のテンプレートで NuGet パッケージ](/nuget/visual-studio-extensibility/visual-studio-templates)