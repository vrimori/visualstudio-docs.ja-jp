---
title: カスタム プロジェクトと項目テンプレートの作成 |Microsoft Docs
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
ms.openlocfilehash: 9e4d938bbfbe1c65882e73630689edff208670e9
ms.sourcegitcommit: 159ed9d4f56cdc1dff2fd19d9dffafe77e46cd4e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2018
ms.locfileid: "53739826"
---
# <a name="create-custom-project-and-item-templates"></a>カスタム プロジェクトと項目テンプレートを作成します。

Visual Studio SDK には、カスタム プロジェクト テンプレートとカスタム項目テンプレートを作成するプロジェクト テンプレートが含まれています。 これらのテンプレートは、いくつかの一般的なパラメーター置換を含めるし、zip ファイルとしてビルドします。 自動的に展開されていないとは、実験用インスタンスで使用できません。 ユーザー テンプレート ディレクトリに生成された zip ファイルをコピーする必要があります。

テンプレートの作成テンプレートを使用してより大きな拡張機能でテンプレートを追加できます。 これにより、ソース ファイルでバージョン管理を実装し、1 つの VSIX パッケージ プロジェクト テンプレートのグループを作成できます。

NuGet パッケージをインストールするためのテンプレートを構成することもできます。 詳細については、次を参照してください。 [Visual Studio テンプレートの NuGet パッケージ](/nuget/visual-studio-extensibility/visual-studio-templates)します。

基本的なテンプレートの作成シナリオで使用する必要があります、**テンプレートのエクスポート**ウィザードで、圧縮されたファイルに出力します。 基本的なテンプレートの作成の詳細については、次を参照してください。[プロジェクトと項目テンプレートを作成する](../ide/creating-project-and-item-templates.md)します。

> [!NOTE]
> Visual Studio 2017 以降、カスタム プロジェクトと項目テンプレートのスキャンは不要になった実行されます。 代わりに、拡張機能では、これらのテンプレートのインストール場所を記述するテンプレート マニフェスト ファイルを提供する必要があります。 Visual Studio 2017 を使用して、VSIX 拡張機能を更新することができます。 MSI を使用して、拡張機能をデプロイする場合は、手動でテンプレート マニフェスト ファイルを生成する必要があります。 詳細については、次を参照してください。[アップグレードのカスタム プロジェクトと項目テンプレートを Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md)します。 テンプレート マニフェスト スキーマについては[Visual Studio テンプレート マニフェスト スキーマ参照](../extensibility/visual-studio-template-manifest-schema-reference.md)します。

## <a name="create-a-project-template"></a>プロジェクト テンプレートを作成します。

1.  プロジェクト テンプレート プロジェクトを作成します。 プロジェクト テンプレートを見つけることができます、**新しいプロジェクト**ダイアログで、Visual Basic または Visual c# で*Extensibility*フォルダー。

     テンプレートが、アイコン、クラス ファイルを生成、 *.vstemplate*という名前を編集可能なプロジェクト ファイルのファイル*ProjectTemplate.vbproj*または*ProjectTemplate.csproj*、および他のプロジェクトの種類によって通常生成されるファイルこのような*resources.resx*ファイル、 *AssemblyInfo*ファイル、および *.settings*ファイル。 各コード ファイルには、適切な場所の一般的なパラメーターの代用が含まれています。

2.  追加し、プロジェクトの必要に応じてプロジェクトから項目を削除します。 編集可能なプロジェクト ファイルを削除しないでください、 *AssemblyInfo*ファイル、または *.vstemplate*ファイル。

3.  更新プログラム、 *.vstemplate*ファイルの追加と削除を反映するようにします。 [プロジェクト](../extensibility/project-element-visual-studio-templates.md)要素を含める必要があります、 [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)テンプレートに含まれる各ファイルの要素。

4.  コード ファイルとその他のユーザーに表示されるコンテンツを変更し、適切なパラメーター置換を追加します。

5.  必要に応じて生成されるコンテンツを変更します。

6.  プロジェクトをビルドします。

     Visual Studio によって作成、 *.zip*テンプレートが含まれるファイル。 展開されていないと、実験用インスタンスで使用できなくなります。

## <a name="create-an-item-template"></a>項目テンプレートを作成します。

1.  項目テンプレート プロジェクトを作成します。

     テンプレートが、アイコン、クラス ファイルを生成、 *.vstemplate*ファイル、および*AssemblyInfo*ファイル。 クラス ファイルには、いくつかの一般的なパラメーターの代替文字列が含まれています。

2.  追加し、プロジェクトの必要に応じてプロジェクトから項目を削除します。

3.  更新プログラム、 *.vstemplate*ファイルの追加と削除を反映するようにします。 [プロジェクト](../extensibility/project-element-visual-studio-templates.md)要素を含める必要があります、 [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)テンプレートに含まれる各ファイルの要素。

4.  コード ファイルとその他のユーザーに表示されるコンテンツを変更し、適切なパラメーター置換を追加します。

5.  必要に応じて生成されるコンテンツを変更します。

6.  プロジェクトをビルドします。

     Visual Studio には、テンプレートを含む圧縮ファイルが作成されます。 展開されていないと、実験用インスタンスで使用できなくなります。

## <a name="deployment"></a>配置

### <a name="to-deploy-the-project-or-item-template"></a>プロジェクトまたは項目テンプレートをデプロイするには

1.  VSIX プロジェクトを作成する。 詳細については、次を参照してください。 [VSIX プロジェクト テンプレート](../extensibility/vsix-project-template.md)します。

2.  VSIX プロジェクトをスタートアップ プロジェクトとして設定します。 **ソリューション エクスプ ローラー**、選択、VSIX プロジェクト ノードを右クリックし、**スタートアップ プロジェクトとして設定**します。

3.  VSIX プロジェクトの資産として、プロジェクト テンプレート プロジェクトを設定します。 開く、 *.vsixmanifest*ファイル。 移動して、**資産** タブでをクリックし、**新規**します。

    1.  設定、**型**フィールドを**Microsoft.VisualStudio.ProjectTemplate**または **[microsoft.visualstudio.itemtemplate]** します。

    2.  ソースの選択、**現在のソリューションでプロジェクトを**オプション、およびテンプレートが含まれているプロジェクトを選択します。

4.  ソリューションをビルドし、キーを押して**F5**します。 実験用インスタンスが表示されます。

5.  プロジェクト テンプレート プロジェクトの場合に、記載されて、プロジェクト テンプレートを表示する必要があります、**新しいプロジェクト**ダイアログ (**ファイル** > **新規** >  **プロジェクト**)、Visual c# または Visual Basic ノード。 項目テンプレート プロジェクトでは、記載、項目テンプレートが表示されます、**新しい項目の追加**ダイアログ。 表示する、**新しい項目の追加**ダイアログ ボックスから、**ソリューション エクスプ ローラー**プロジェクト ノードを選択して、クリックして**追加** > **新しい項目の**).

## <a name="see-also"></a>関連項目

[Visual Studio テンプレート参照](../ide/creating-project-and-item-templates.md)
[Visual Studio テンプレートの NuGet パッケージ](/nuget/visual-studio-extensibility/visual-studio-templates)