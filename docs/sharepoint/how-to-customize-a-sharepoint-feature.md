---
title: "方法: SharePoint フィーチャーをカスタマイズ |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.RAD.FeatureDesigner.SwitchView
- VS.SharePointTools.RAD.featureDesigner.Manifest
- VS.SharePointTools.RAD.FeatureDesignerProperties
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: adb4283a56715da704df8991543ea89c6cbc79a4
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-customize-a-sharepoint-feature"></a>方法: SharePoint フィーチャーをカスタマイズする
  作成し、Visual Studio で、フィーチャー デザイナーを使用して、SharePoint の機能をカスタマイズできます。 たとえば、フィーチャーのスコープを設定でき、依存関係として他の機能を追加できます。 既定では、ソリューション エクスプ ローラーまたは SharePoint の パッケージ エクスプ ローラーで、新しい機能を追加するときに、フィーチャー デザイナーが開きます。  
  
## <a name="opening-the-feature-designer"></a>フィーチャー デザイナーを開く  
 追加するか、フィーチャー デザイナーを使用して機能を SharePoint プロジェクト項目を削除します。  
  
#### <a name="to-open-the-feature-designer"></a>開くには、フィーチャー デザイナー  
  
1.  **ソリューション エクスプ ローラー**、展開**機能**します。  
  
2.  ダブルクリックして、 *Feature1*アイテム、または、ショートカット メニューを開き、 *Feature1*項目し、**ビュー デザイナー**です。  
  
## <a name="viewing-the-packaged-manifest-file"></a>パッケージ マニフェスト ファイルを表示します。  
 フィーチャー デザイナーを使用して、変更および機能 (feature.xml) のパッケージ マニフェスト ファイルを生成することができます。 次に、Visual Studio でこのファイルの XML コードを表示できます。  
  
#### <a name="to-view-the-packaged-manifest-file"></a>パッケージ マニフェスト ファイルを表示するには  
  
1.  **フィーチャー デザイナー**、選択、**マニフェスト**タブです。  
  
#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>ソリューション エクスプ ローラーを使用してパッケージのマニフェスト ファイルを表示するには  
  
1.  **ソリューション エクスプ ローラー**、選択、 **すべてのファイル**アイコン。  
  
2.  機能を展開、展開、FeatureName.feature を展開し、開きます、 *FeatureName*です。Template.xml ファイルです。  
  
    > [!NOTE]  
    >  機能テンプレート マニフェスト XML ファイルを開くし、ファイルは自動的に検証エラー一覧 ウィンドウに表示される警告を無視することができます。  
  
## <a name="changing-the-manifest-template"></a>マニフェスト テンプレートの変更  
 Visual Studio XML エディターまたはマニフェスト テンプレート ペインでフィーチャー マニフェスト ファイルの XML コードを変更することができます。 XML コードを変更するは、機能のパッケージ マニフェスト ファイルにマージされます。 たとえば、フィーチャーのプロパティをカスタマイズするマニフェスト テンプレートを変更することがあります。  
  
#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>XML エディターを使用して、マニフェスト テンプレートを変更するには  
  
1.  **フィーチャー デザイナー**、選択、**マニフェスト** タブで、展開、**オプションの編集** ノードを選択し、 **XML エディターで開いている**リンクします。  
  
     XML への変更は、パッケージ マニフェスト ファイルにマージされます。  
  
#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>マニフェスト テンプレート ペインを使用して、マニフェスト テンプレートを変更するには  
  
1.  **フィーチャー デザイナー**、選択、**マニフェスト** タブで、展開、**編集オプション**ノードを展開し、マニフェスト テンプレート ペインに表示する XML を変更します。  
  
     XML への変更が表示される、**プレビューのパッケージ化されたマニフェスト**ウィンドウです。  
  
## <a name="overwriting-the-packaged-manifest-file"></a>パッケージ マニフェスト ファイルを上書きします。  
 フィーチャー デザイナーを無効にし、feature.xml ファイルを手動で作成できます。 この手順を実行する最初に、フィーチャー デザイナーの現在の設定は、機能のテンプレート XML ファイルに保存されます。 次に、変更したり、XML コードを上書きします。  
  
> [!NOTE]  
>  追加またはフィーチャー デザイナーが無効になっているときに、XML ファイルの SharePoint プロジェクト項目を削除した場合、それらのプロジェクト項目はパッケージ化されません。  
  
#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>デザイナーを無効にすると、パッケージ マニフェスト ファイルを上書きするには  
  
1.  **フィーチャー デザイナー**、選択、**マニフェスト**タブです。  
  
2.  展開、**編集オプション** ノードを選択、**上書き生成された XML と編集、XML エディターでマニフェスト**リンクをクリックして、 **はい**ボタンをクリックします。  
  
     テンプレートは、現在のパッケージ マニフェスト ファイルで更新されます。  
  
## <a name="enabling-the-feature-designer"></a>フィーチャー デザイナーを有効にします。  
 Feature.xml ファイルをカスタマイズするフィーチャー デザイナーを再度有効にすることができます。  
  
#### <a name="to-re-enable-the-designer"></a>デザイナーを再度有効にするには  
  
1.  **フィーチャー デザイナー**、選択、**マニフェストの編集を破棄してデザイナーを再度有効に**リンクをクリックして、**はい**ボタンをクリックします。  
  
2.  元のテキストで、テンプレートが更新され、XML に変更は失われます。  
  
## <a name="see-also"></a>参照  
 [SharePoint ソリューションのパッケージ化と配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  