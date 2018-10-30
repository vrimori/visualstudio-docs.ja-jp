---
title: '方法: 追加およびその他のアセンブリの削除 |Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.CustomAssembly
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4178f1ca5a437c52754199d26a6d39023193aaf8
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219147"
---
# <a name="how-to-add-and-remove-additional-assemblies"></a>方法: 追加およびその他のアセンブリの削除
  SharePoint パッケージが機能またはデータについて他のアセンブリに依存している場合、そのアセンブリをソリューション パッケージ (.wsp) に追加できます。 パッケージをインストールする際は、カスタム アセンブリがインストールされているかどうかが、SharePoint サーバーによって確認されます。  
  
 アセンブリに関連付けられているセーフ コントロールやクラス リソース ファイルを追加および変更することもできます。  
  
## <a name="add-additional-assemblies-safe-controls-and-class-resources"></a>追加のアセンブリ、セーフ コントロール、およびクラス リソースを追加します。  
 SharePoint ソリューション パッケージにアセンブリを追加できます。 サンドボックス ソリューションの追加アセンブリは、グローバル アセンブリ キャッシュに配置されますが、サンドボックス ソリューションの SharePoint プロジェクト項目はコンテンツ データベースに追加されます。 これらの追加アセンブリにセーフ コントロールやクラス リソースを追加することもできます。 安全なコントロールの詳細については、次を参照してください。 [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)またはで"SafeControl エントリの作成" [SharePoint Foundation の Web パーツを配置する](http://go.microsoft.com/fwlink/?LinkId=245505)します。  
  
#### <a name="to-add-an-existing-assembly"></a>既存のアセンブリを追加するには  
  
1.  開く、**パッケージ デザイナー**します。 詳細については、次を参照してください。[方法: SharePoint ソリューション パッケージをカスタマイズ](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)します。  
  
2.  選択、**詳細**タブ。  
  
3.  選択、**追加**ボタンをクリックし、**既存アセンブリの追加**一覧から。  
  
     **既存アセンブリの追加** ダイアログ ボックスが表示されます。  
  
4.  省略記号 (![ASP.NET モバイル デザイナー楕円](../sharepoint/media/mwellipsis.gif "ASP.NET モバイル デザイナー楕円")) を追加するアセンブリを選択します。 移植性を考慮して、選択したアセンブリへの相対パスを使用することをお勧めします。  
  
5.  **配置ターゲット**、選択、 **GlobalAssemblyCache**オプション ボタンをクリックする、グローバル アセンブリ キャッシュにアセンブリを配置するか、選択、 **WebApplication**オプションSharePoint を実行しているサーバーの WebApplication フォルダーにアセンブリを配置するボタンをクリックします。  
  
#### <a name="to-add-an-assembly-from-project-output"></a>プロジェクトの出力からアセンブリを追加するには  
  
1.  開く、**パッケージ デザイナー**します。  
  
     詳細については、次を参照してください。[方法: SharePoint ソリューション パッケージをカスタマイズ](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)します。  
  
2.  選択、**詳細**タブ。  
  
3.  選択、**追加**ボタンをクリックし、**プロジェクト出力からアセンブリを追加**一覧から。  
  
     **プロジェクト出力からアセンブリを追加** ダイアログ ボックスが表示されます。  
  
4.  **ソース プロジェクト**して、追加するソース プロジェクトを選択します。  
  
5.  **配置ターゲット**、選択、 **GlobalAssemblyCache**オプション ボタンをクリックする、グローバル アセンブリ キャッシュにアセンブリを配置するか、選択、 **WebApplication**オプションSharePoint を実行しているサーバーの WebApplication フォルダーにアセンブリを配置するボタンをクリックします。  
  
#### <a name="to-add-a-safe-control"></a>セーフ コントロールを追加するには  
  
1.  開く、**既存のアセンブリの編集** ダイアログ ボックス。 これを実現するには、パッケージ デザイナーを開き、**詳細**] タブで、アセンブリを選択し、[、**編集**ボタンをクリックします。  
  
2.  **安全なコントロール**ウィンドウで、選択、**ここをクリックすると、新しい項目を追加する**ボタンをクリックします。  
  
3.  **アセンブリ名**列で、アセンブリの名前を入力します。  
  
4.  **Namespace**列で、安全なコントロールの名前空間の名前を入力します。  
  
5.  **型名**列、型の名前を入力します。  
  
#### <a name="to-add-a-class-resource"></a>クラス リソースを追加するには  
  
1.  開く、**既存のアセンブリの編集** ダイアログ ボックス。 これを実現するには、パッケージ デザイナーを開き、**詳細**] タブで、アセンブリを選択し、[、**編集**ボタンをクリックします。  
  
2.  **クラス リソース**ウィンドウで、選択、**ここをクリックすると、新しい項目を追加する**ボタンをクリックします。  
  
3.  **ファイル名**列で、省略記号 (![ASP.NET モバイル デザイナー楕円](../sharepoint/media/mwellipsis.gif "ASP.NET モバイル デザイナー楕円")) を追加するクラスのリソースを選択します。  
  
## <a name="delete-custom-assemblies"></a>カスタム アセンブリを削除します。  
 SharePoint パッケージからアセンブリを削除したり、既存のアセンブリからセーフ コントロールやクラス リソースを削除することもできます。  
  
#### <a name="to-delete-an-existing-assembly"></a>既存のアセンブリを削除するには  
  
1.  開く、**パッケージ デザイナー**します。 詳細については、次を参照してください。[方法: SharePoint ソリューション パッケージをカスタマイズ](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)します。  
  
2.  選択、**詳細**タブ。  
  
3.  **追加アセンブリ**ウィンドウで、削除するカスタム アセンブリを選択します。  
  
4.  選択、**削除**ボタンをクリックします。  
  
#### <a name="to-delete-a-safe-control-for-an-assembly"></a>アセンブリの安全なコントロールを削除するには  
  
1.  開く、**既存のアセンブリの編集** ダイアログ ボックス。 これを実現するには、パッケージ デザイナーを開き、**詳細**] タブで、アセンブリを選択し、[、**編集**ボタンをクリックします。  
  
2.  削除する安全なコントロールをクリックします。  
  
3.  Del キーを押します。  
  
#### <a name="to-delete-a-class-resource-for-an-assembly"></a>アセンブリのクラス リソースを削除するには  
  
1.  開く、**既存のアセンブリの編集** ダイアログ ボックス。 これを実現するには、パッケージ デザイナーを開き、**詳細**] タブで、アセンブリを選択し、[、**編集**ボタンをクリックします。  
  
2.  削除するクラス リソースをクリックします。  
  
3.  Del キーを押します。  
  
## <a name="see-also"></a>関連項目
 [SharePoint の機能を作成します。](../sharepoint/creating-sharepoint-features.md)   
 [方法: SharePoint フィーチャーをカスタマイズ](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [方法: 項目を SharePoint の機能を追加および削除](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
  
