---
title: '方法: SharePoint フィーチャーをカスタマイズ |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.FeatureDesigner.SwitchView
- VS.SharePointTools.RAD.featureDesigner.Manifest
- VS.SharePointTools.RAD.FeatureDesignerProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 867eb1fd64a7318d460a387ededd39e4f188d445
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54868106"
---
# <a name="how-to-customize-a-sharepoint-feature"></a>方法: SharePoint フィーチャーをカスタマイズします。
  作成し、Visual Studio でフィーチャー デザイナーを使用して、SharePoint の機能をカスタマイズできます。 たとえば、フィーチャーのスコープを設定でき、依存関係としてその他の機能を追加できます。 既定では、ソリューション エクスプ ローラーまたは SharePoint の パッケージ エクスプ ローラーで新しい機能を追加するときに、フィーチャー デザイナーが開きます。  
  
## <a name="opening-the-feature-designer"></a>フィーチャー デザイナーを開く  
 追加またはフィーチャー デザイナーを使用して機能する SharePoint プロジェクト項目を削除できます。  
  
#### <a name="to-open-the-feature-designer"></a>フィーチャー デザイナーを開く
  
1.  **ソリューション エクスプ ローラー**、展開**機能**します。  
  
2.  ダブルクリックして、 *Feature1*項目、または、ショートカット メニューを開き、 *Feature1*項目選び、**ビュー デザイナー**します。  
  
## <a name="view-the-packaged-manifest-file"></a>パッケージ マニフェスト ファイルを表示します。  
 変更および機能のパッケージ マニフェスト ファイルを生成するフィーチャー デザイナーを使用することができます (*feature.xml*)。 次に、Visual Studio でこのファイルの XML コードを表示できます。  
  
#### <a name="to-view-the-packaged-manifest-file"></a>パッケージ マニフェスト ファイルを表示するには  
  
1.  **フィーチャー デザイナー**、選択、**マニフェスト**タブ。  
  
#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>ソリューション エクスプ ローラーを使用してパッケージのマニフェスト ファイルを表示するには  
  
1.  **ソリューション エクスプ ローラー**、選択、 **すべてのファイル**アイコン。  
  
2.  機能を展開し、展開を FeatureName.feature を展開し、開く、  *\<FeatureName >。Template.xml*ファイル。  
  
    > [!NOTE]  
    >  機能のテンプレート マニフェスト XML ファイルを開くし、ファイルは自動的に検証エラー一覧 ウィンドウに表示される警告を無視できます。  
  
## <a name="change-the-manifest-template"></a>マニフェスト テンプレートを変更します。  
 Visual Studio XML エディターまたはマニフェスト テンプレート ペインでフィーチャー マニフェスト ファイルの XML コードを変更することができます。 XML コードに対する変更は、機能のパッケージ マニフェスト ファイルにマージされます。 たとえば、フィーチャーのプロパティをカスタマイズするマニフェスト テンプレートを変更する可能性があります。  
  
#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>XML エディターを使用して、マニフェスト テンプレートを変更するには  
  
1.  **フィーチャー デザイナー**、選択、**マニフェスト** タブで、展開、**オプションの編集**ノードを選択し、 **XML エディターで開いている**リンク。  
  
     XML への変更は、パッケージ マニフェスト ファイルにマージされます。  
  
#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>マニフェスト テンプレート ペインを使用して、マニフェスト テンプレートを変更するには  
  
1.  **フィーチャー デザイナー**、選択、**マニフェスト** タブで、展開、**編集オプション**ノード、およびマニフェスト テンプレート ペインに表示される XML を変更します。  
  
     XML への変更に表示される、**プレビューのパッケージ化されたマニフェスト**ウィンドウ。  
  
## <a name="overwrite-the-packaged-manifest-file"></a>パッケージ マニフェスト ファイルを上書き  
 フィーチャー デザイナーを無効にし、作成することができます、 *feature.xml*ファイルを手動でします。 この手順を実行する最初にフィーチャー デザイナーの現在の設定は、機能のテンプレート XML ファイルに保存されます。 次に、変更したり、XML コードを上書きできます。  
  
> [!NOTE]  
>  追加またはフィーチャー デザイナーを無効にして、XML ファイルの SharePoint プロジェクト アイテムを削除する場合、これらのプロジェクト項目はパッケージ化されません。  
  
#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>デザイナーを無効にして、パッケージ マニフェスト ファイルを上書きするには  
  
1.  **フィーチャー デザイナー**、選択、**マニフェスト**タブ。  
  
2.  展開、**オプションの編集**ノード、選択、**上書き生成された XML と編集マニフェスト XML エディターで**リンクをクリックして、**はい**ボタン。  
  
     テンプレートは、現在のパッケージ マニフェスト ファイルで更新されます。  
  
## <a name="enable-the-feature-designer"></a>フィーチャー デザイナーを有効にします。  
 カスタマイズするフィーチャー デザイナーを再度有効にできる、 *feature.xml*ファイル。  
  
#### <a name="to-re-enable-the-designer"></a>デザイナーを再度有効にするには  
  
1.  **フィーチャー デザイナー**、選択、**マニフェストの編集を破棄し、デザイナーを再度有効に**リンクをクリックして、**はい**ボタン。  
  
2.  元のテキストで、テンプレートが更新され、XML への変更は失われます。  
  
## <a name="see-also"></a>関連項目
 [パッケージ化し、SharePoint ソリューションのデプロイ](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
