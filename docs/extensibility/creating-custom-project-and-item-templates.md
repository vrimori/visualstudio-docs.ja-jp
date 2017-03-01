---
title: "カスタムのプロジェクトおよび項目テンプレートを作成する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
caps.latest.revision: 10
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
ms.sourcegitcommit: 512014c5070e4314ad2b7d0e8c5c404c43f32cd9
ms.openlocfilehash: be53e0aa5179a38f9c2079513661607b45767a11
ms.lasthandoff: 02/22/2017

---
# <a name="creating-custom-project-and-item-templates"></a>カスタムのプロジェクトおよび項目テンプレートを作成します。
Visual Studio SDK には、カスタム プロジェクト テンプレートとカスタム項目テンプレートを作成するプロジェクト テンプレートが含まれています。 これらのテンプレートは、いくつかの一般的なパラメーター置換を含む、zip ファイルとして構築します。 これらは自動的に展開されていないは実験用インスタンスで使用できません。 Zip ファイルをコピーする必要があります場所へのファイルを  
  
 テンプレートの作成テンプレートを使用して、大規模な拡張機能のテンプレートを追加できます。 これにより、ソース ファイルにバージョン管理を実装し、プロジェクト テンプレートのグループを&1; つの VSIX パッケージにビルドできます。  
  
 基本的なテンプレートの作成シナリオで使用する必要があります、**テンプレートのエクスポート**ウィザードで、圧縮されたファイルに出力します。 基本的なテンプレートの作成の詳細については、次を参照してください。[を作成するプロジェクトと項目テンプレート](../ide/creating-project-and-item-templates.md)します。  
  
 Visual Studio 2017 以降、カスタムのプロジェクトおよび項目テンプレートのスキャンが不要になった実行されます。 代わりに、拡張機能では、これらのテンプレートのインストール場所を記述するマニフェスト ファイルのテンプレートを提供する必要があります。 Visual Studio 2017 を使用して、VSIX 拡張を更新できます。 MSI を使用して、拡張機能を展開する場合は、テンプレートのマニフェスト ファイルを手動で生成する必要があります。 詳細については、次を参照してください。[をアップグレードするカスタムのプロジェクトおよび項目テンプレートを Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md)します。 テンプレートのマニフェスト スキーマの詳細は「 [Visual Studio テンプレート マニフェスト スキーマ リファレンス](../extensibility/visual-studio-template-manifest-schema-reference.md)します。  
  
## <a name="creating-a-project-template"></a>プロジェクト テンプレートを作成します。  
  
1.  プロジェクト テンプレート プロジェクトを作成します。 プロジェクト テンプレートを見つけることができます、**新しいプロジェクト**ダイアログで、Visual Basic または Visual c# で**拡張**フォルダーです。  
  
     テンプレートは、クラス ファイル、アイコン、.vstemplate ファイル、名前付き ProjectTemplate.vbproj または ProjectTemplate.csproj、編集可能なプロジェクト ファイルとその他のプロジェクトの種類によって通常生成されるいくつかのファイル、resources.resx ファイルがこのような AssemblyInfo ファイルでは、および .settings ファイルを生成します。 各コード ファイルには、適切な場所の一般的なパラメーター置換が含まれています。  
  
2.  追加し、プロジェクトに必要なプロジェクトから項目を削除します。 編集可能なプロジェクト ファイル、AssemblyInfo ファイルまたは .vstemplate ファイルを削除しません。  
  
3.  任意の追加と削除を反映するように、.vstemplate ファイルを更新します。 [プロジェクト](../extensibility/project-element-visual-studio-templates.md)要素を含める必要があります、 [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)テンプレートに含まれる各ファイルの要素。  
  
4.  コード ファイルおよびその他のユーザー向けのコンテンツを変更し、適切なパラメーター置換を追加します。  
  
5.  必要に応じて生成されるコンテンツを変更します。  
  
6.  プロジェクトをビルドします。  
  
     Visual Studio では、テンプレートが含まれている .zip ファイルを作成します。 デプロイされていないと、実験用インスタンスで使用不可であります。  
  
## <a name="creating-an-item-template"></a>項目テンプレートを作成します。  
  
1.  項目テンプレート プロジェクトを作成します。  
  
     テンプレートは、クラス ファイル、アイコン、.vstemplate ファイルおよび AssemblyInfo ファイルを生成します。 クラス ファイルには、いくつかの一般的なパラメーターの代替文字列が含まれています。  
  
2.  追加し、プロジェクトに必要なプロジェクトから項目を削除します。  
  
3.  任意の追加と削除を反映するように、.vstemplate ファイルを更新します。 [プロジェクト](../extensibility/project-element-visual-studio-templates.md)要素を含める必要があります、 [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)テンプレートに含まれる各ファイルの要素。  
  
4.  コード ファイルおよびその他のユーザー向けのコンテンツを変更し、適切なパラメーター置換を追加します。  
  
5.  必要に応じて生成されるコンテンツを変更します。  
  
6.  プロジェクトをビルドします。  
  
     Visual Studio では、テンプレートが含まれている圧縮ファイルを作成します。 デプロイされていないと、実験用インスタンスで使用不可であります。  
  
## <a name="deployment"></a>配置  
  
#### <a name="to-deploy-the-project-or-item-template"></a>プロジェクトまたは項目テンプレートをデプロイするには  
  
1.  VSIX プロジェクトを作成する。 詳細については、次を参照してください。 [VSIX プロジェクトのテンプレート](../extensibility/vsix-project-template.md)します。  
  
2.  VSIX プロジェクトをスタートアップ プロジェクトとして設定します。 **ソリューション エクスプ ローラー**、選択、VSIX プロジェクト ノードを右クリックし、**スタートアップ プロジェクトとして設定**します。  
  
3.  VSIX プロジェクトのアセットとしてのプロジェクト テンプレート プロジェクトを設定します。 .Vsixmanifest ファイルを開きます。 移動して、**資産** タブでをクリックし、**新規**します。  
  
    1.  設定、**型**フィールドを**[microsoft.visualstudio.projecttemplate]**または**[microsoft.visualstudio.itemtemplate]**します。  
  
    2.  ソースの選択、**現在のソリューション内のプロジェクト**にして、テンプレートが含まれるプロジェクトを選択します。  
  
4.  ソリューションをビルドし、F5 キーを押します。 実験用インスタンスが表示されます。  
  
5.  プロジェクト テンプレート プロジェクトの場合に示されているプロジェクト テンプレートを表示する必要があります、**新しいプロジェクト**ダイアログ (**ファイル/新しい/project**) では、Visual c# または Visual Basic のノードです。 項目テンプレート プロジェクトの新しい項目の追加] ダイアログに表示項目テンプレートを表示する必要があります (で、**ソリューション エクスプ ローラー**プロジェクト ノードを選択してクリックして**追加/[新しい項目の**)。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio テンプレート参照](../ide/visual-studio-template-reference.md)
