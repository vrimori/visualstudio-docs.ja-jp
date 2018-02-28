---
title: "方法: SharePoint ソリューション パッケージをカスタマイズ |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerAdvanced
- VS.SharePointTools.RAD.PackageDesigner.Manifest
- VS.SharePointTools.RAD.PackageDesignerProperties
- VS.SharePointTools.RAD.PackageDesigner.SwitchView
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
ms.openlocfilehash: 277ceea1b908c5819608a1bdf1d6be97c2f6ce77
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-customize-a-sharepoint-solution-package"></a>方法: SharePoint ソリューション パッケージをカスタマイズする
  パッケージ デザイナーを使用して、作成およびパッケージ (.wsp) をカスタマイズすることができます。 たとえば、SharePoint プロジェクト項目と機能の追加、Web サーバーがソリューションを展開するときのリセットし、配置サーバーの種類を設定するかどうかを指定できます。  
  
## <a name="opening-the-package-designer"></a>パッケージ デザイナーを開く  
  
#### <a name="to-open-the-package-designer"></a>パッケージ デザイナーを開く  
  
-   **ソリューション エクスプ ローラー**をダブルクリックして**パッケージ**を選択または**ビュー デザイナー**のショートカット メニューの **パッケージ**です。  
  
## <a name="viewing-the-packaged-manifest-file"></a>パッケージ マニフェスト ファイルを表示します。  
 パッケージ デザイナーを使用して、変更およびパッケージのマニフェスト ファイルを生成することができます。 次に、Visual Studio でこのファイルの XML コードを表示できます。  
  
#### <a name="to-view-the-xml-source-file"></a>XML ソース ファイルを表示するには  
  
1.  **パッケージ デザイナー**、選択**マニフェスト**です。  
  
#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>ソリューション エクスプ ローラーを使用してパッケージのマニフェスト ファイルを表示するには  
  
1.  **ソリューション エクスプ ローラー**、選択**すべてのファイル**です。  
  
2.  パッケージを展開し、Package.package を展開し、Package.Template.xml ファイルを開きます。  
  
    > [!NOTE]  
    >  パッケージ テンプレートのマニフェスト XML ファイルを開くし、ファイルが自動的に検証されたら、エラー一覧 ウィンドウに表示される警告を無視することができます。  
  
## <a name="changing-the-manifest-template"></a>マニフェスト テンプレートの変更  
 Visual Studio XML エディターまたはマニフェスト テンプレート ペインでパッケージ マニフェスト ファイルの XML コードを変更することができます。 XML コードを変更するは、パッケージのパッケージ マニフェスト ファイルにマージされます。  
  
#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>XML エディターを使用して、マニフェスト テンプレートを変更するには  
  
1.  **パッケージ デザイナー**、選択、**マニフェスト** タブで、展開、**オプションの編集** ノードを選択し、 **XML エディターで開いている**リンクします。  
  
     XML への変更は、パッケージ マニフェスト ファイルにマージされます。  
  
#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>マニフェスト テンプレート ペインを使用して、マニフェスト テンプレートを変更するには  
  
1.  **パッケージ デザイナー**、選択、**マニフェスト** タブで、展開、**編集オプション**ノードを展開し、マニフェスト テンプレート ペインに表示する XML を変更します。  
  
     XML への変更が表示される、**プレビューのパッケージ化されたマニフェスト**ウィンドウです。  
  
## <a name="overwriting-the-packaged-manifest-file"></a>パッケージ マニフェスト ファイルを上書きします。  
 パッケージ デザイナーを無効にし、マニフェスト xml ファイルを手動で作成できます。 この手順を実行する最初に、パッケージ デザイナーの現在の設定は、パッケージのテンプレート XML ファイルに保存されます。 次に、変更したり、XML コードを上書きします。  
  
> [!NOTE]  
>  追加またはパッケージ デザイナーが無効になっている間は、XML ファイルで SharePoint プロジェクト項目およびフィーチャーを削除した場合は、これらのプロジェクト項目およびフィーチャーはパッケージ化されます。  
  
#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>デザイナーを無効にすると、パッケージ マニフェスト ファイルを上書きするには  
  
1.  **パッケージ デザイナー**、選択、**マニフェスト**タブです。  
  
2.  である必要があります。  
  
3.  展開、**編集オプション** ノードを選択、**上書き生成された XML と編集、XML エディターでマニフェスト**リンクをクリックして、 **はい**ボタンをクリックします。  
  
     テンプレートは、現在のパッケージ マニフェスト ファイルで更新されます。  
  
## <a name="enabling-the-package-designer"></a>パッケージ デザイナーを有効にします。  
 マニフェスト xml ファイルをカスタマイズする、パッケージ デザイナーを再度有効にすることができます。  
  
#### <a name="to-re-enable-the-designer"></a>デザイナーを再度有効にするには  
  
1.  **パッケージ デザイナー**、選択、**マニフェストの編集を破棄してデザイナーを再度有効に**リンクをクリックして、**はい**ボタンをクリックします。  
  
     元のテキストで、テンプレートが更新され、XML に変更は失われます。  
  
## <a name="see-also"></a>参照  
 [SharePoint ソリューションのパッケージ化と配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  