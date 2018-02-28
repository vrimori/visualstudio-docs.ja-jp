---
title: "方法: 追加およびその他のアセンブリを削除する |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
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
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 13ea5388a7b4ce2d1a045dec6339dc59e5c68393
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-and-remove-additional-assemblies"></a>方法: アセンブリを追加および削除する
  SharePoint パッケージが機能またはデータについて他のアセンブリに依存している場合、そのアセンブリをソリューション パッケージ (.wsp) に追加できます。 パッケージをインストールする際は、カスタム アセンブリがインストールされているかどうかが、SharePoint サーバーによって確認されます。  
  
 アセンブリに関連付けられているセーフ コントロールやクラス リソース ファイルを追加および変更することもできます。  
  
## <a name="adding-additional-assemblies-safe-controls-and-class-resources"></a>アセンブリ、セーフ コントロール、およびクラス リソースの追加  
 SharePoint ソリューション パッケージにアセンブリを追加できます。 サンドボックス ソリューションの追加アセンブリは、グローバル アセンブリ キャッシュに配置されますが、サンドボックス ソリューションの SharePoint プロジェクト項目はコンテンツ データベースに追加されます。 これらの追加アセンブリにセーフ コントロールやクラス リソースを追加することもできます。 安全なコントロールの詳細については、次を参照してください。[を提供するパッケージとプロジェクト項目での展開情報](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)または"を作成する、SafeControl エントリ"で[SharePoint Foundation の Web パーツを配置する](http://go.microsoft.com/fwlink/?LinkId=245505)です。  
  
#### <a name="to-add-an-existing-assembly"></a>既存のアセンブリを追加するには  
  
1.  開く、**パッケージ デザイナー**です。 詳細については、次を参照してください。[する方法: SharePoint ソリューション パッケージをカスタマイズ](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)です。  
  
2.  選択、**詳細**タブです。  
  
3.  選択、**追加**ボタンをクリックし、**既存のアセンブリの追加**一覧からです。  
  
     **既存のアセンブリの追加** ダイアログ ボックスが表示されます。  
  
4.  省略記号ボタンを選択 (![ASP.NET モバイル デザイナー楕円](../sharepoint/media/mwellipsis.gif "ASP.NET モバイル デザイナー楕円"))、追加するアセンブリを選択します。 移植性を考慮して、選択したアセンブリへの相対パスを使用することをお勧めします。  
  
5.  **配置ターゲット**、選択、 **GlobalAssemblyCache** 、グローバル アセンブリ キャッシュにアセンブリを配置またはを選択するオプション ボタン、 **WebApplication**オプションSharePoint を実行しているサーバーの WebApplication フォルダーにアセンブリを配置するボタンをクリックします。  
  
#### <a name="to-add-an-assembly-from-project-output"></a>プロジェクトの出力からアセンブリを追加するには  
  
1.  開く、**パッケージ デザイナー**です。  
  
     詳細については、次を参照してください。[する方法: SharePoint ソリューション パッケージをカスタマイズ](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)です。  
  
2.  選択、**詳細**タブです。  
  
3.  選択、**追加**ボタンをクリックし、**プロジェクト出力からアセンブリを追加**一覧からです。  
  
     **プロジェクト出力からアセンブリを追加** ダイアログ ボックスが表示されます。  
  
4.  **ソース プロジェクト**一覧、および追加するソース プロジェクトを選択します。  
  
5.  **配置ターゲット**、選択、 **GlobalAssemblyCache** 、グローバル アセンブリ キャッシュにアセンブリを配置またはを選択するオプション ボタン、 **WebApplication**オプションSharePoint を実行しているサーバーの WebApplication フォルダーにアセンブリを配置するボタンをクリックします。  
  
#### <a name="to-add-a-safe-control"></a>セーフ コントロールを追加するには  
  
1.  開く、**既存のアセンブリの編集** ダイアログ ボックス。 これを実現する、パッケージ デザイナーを開き、選択、 **詳細設定**  タブで、アセンブリを選択しを選択し、**編集**ボタンをクリックします。  
  
2.  **安全なコントロール** ウィンドウで、選択、**ここをクリックして、新しい項目を追加する**ボタンをクリックします。  
  
3.  **アセンブリ名**列アセンブリの名前を入力します。  
  
4.  **Namespace**列で、安全なコントロールの名前空間の名前を入力します。  
  
5.  **型名**列で、型の名前を入力します。  
  
#### <a name="to-add-a-class-resource"></a>クラス リソースを追加するには  
  
1.  開く、**既存のアセンブリの編集** ダイアログ ボックス。 これを実現する、パッケージ デザイナーを開き、選択、 **詳細設定**  タブで、アセンブリを選択しを選択し、**編集**ボタンをクリックします。  
  
2.  **クラス リソース** ウィンドウで、選択、**ここをクリックして、新しい項目を追加する**ボタンをクリックします。  
  
3.  **ファイル名**列で、選択、省略記号 (![ASP.NET モバイル デザイナー楕円](../sharepoint/media/mwellipsis.gif "ASP.NET モバイル デザイナー楕円"))、クラス リソースを追加するを選択するとします。  
  
## <a name="deleting-custom-assemblies"></a>カスタム アセンブリの削除  
 SharePoint パッケージからアセンブリを削除したり、既存のアセンブリからセーフ コントロールやクラス リソースを削除することもできます。  
  
#### <a name="to-delete-an-existing-assembly"></a>既存のアセンブリを削除するには  
  
1.  開く、**パッケージ デザイナー**です。 詳細については、次を参照してください。[する方法: SharePoint ソリューション パッケージをカスタマイズ](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)です。  
  
2.  選択、**詳細**タブです。  
  
3.  **追加アセンブリ** ウィンドウで、削除するカスタム アセンブリを選択します。  
  
4.  選択、**削除**ボタンをクリックします。  
  
#### <a name="to-delete-a-safe-control-for-an-assembly"></a>アセンブリの安全なコントロールを削除するには  
  
1.  開く、**既存のアセンブリの編集** ダイアログ ボックス。 これを実現する、パッケージ デザイナーを開き、選択、 **詳細設定**  タブで、アセンブリを選択しを選択し、**編集**ボタンをクリックします。  
  
2.  削除する安全なコントロールをクリックします。  
  
3.  Del キーを押します。  
  
#### <a name="to-delete-a-class-resource-for-an-assembly"></a>アセンブリのクラス リソースを削除するには  
  
1.  開く、**既存のアセンブリの編集** ダイアログ ボックス。 これを実現する、パッケージ デザイナーを開き、選択、 **詳細設定**  タブで、アセンブリを選択しを選択し、**編集**ボタンをクリックします。  
  
2.  削除するクラス リソースをクリックします。  
  
3.  Del キーを押します。  
  
## <a name="see-also"></a>参照  
 [SharePoint フィーチャーの作成](../sharepoint/creating-sharepoint-features.md)   
 [方法: SharePoint フィーチャーをカスタマイズ](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [方法: SharePoint フィーチャーの項目を追加および削除する](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
  
  