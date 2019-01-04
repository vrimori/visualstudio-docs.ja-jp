---
title: '方法: SharePoint ソリューション パッケージをカスタマイズ |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerAdvanced
- VS.SharePointTools.RAD.PackageDesigner.Manifest
- VS.SharePointTools.RAD.PackageDesignerProperties
- VS.SharePointTools.RAD.PackageDesigner.SwitchView
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 85140f8d85c90d2b58df10a63f50c117e10eb8bd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53835397"
---
# <a name="how-to-customize-a-sharepoint-solution-package"></a>方法: SharePoint ソリューション パッケージをカスタマイズします。
  パッケージ デザイナーを使用して作成およびパッケージをカスタマイズすることができます (*.wsp*)。 たとえば、SharePoint プロジェクト項目と機能の追加、Web サーバーが、ソリューションを展開するときにリセットし、配置サーバーの種類を設定するかどうかを指定できます。  
  
## <a name="open-the-package-designer"></a>パッケージ デザイナーを開く  
  
#### <a name="to-open-the-package-designer"></a>パッケージ デザイナーを開く
  
-   **ソリューション エクスプ ローラー**、ダブルクリック**パッケージ**、選択または**ビュー デザイナー**のショートカット メニューの **パッケージ**。  
  
## <a name="view-the-packaged-manifestffile"></a>パッケージ化された manifestfFile を表示します。  
 パッケージ デザイナーを使用して、変更し、パッケージ マニフェスト ファイルを生成することができます。 次に、Visual Studio でこのファイルの XML コードを表示できます。  
  
#### <a name="to-view-the-xml-source-file"></a>XML ソース ファイルを表示するには  
  
1.  **パッケージ デザイナー**、選択**マニフェスト**します。  
  
#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>ソリューション エクスプ ローラーを使用してパッケージのマニフェスト ファイルを表示するには  
  
1.  **ソリューション エクスプローラー**で、**[すべてのファイルを表示]** をクリックします。  
  
2.  パッケージを展開し、Package.package を展開し、開きます、 *Package.Template.xml*ファイル。  
  
    > [!NOTE]  
    >  パッケージ テンプレートについてはマニフェスト XML ファイルを開くし、ファイルが自動的に検証、エラー一覧 ウィンドウに表示される警告を無視することができます。  
  
## <a name="change-the-manifest-template"></a>マニフェスト テンプレートを変更します。  
 Visual Studio XML エディターまたはマニフェスト テンプレート ペインで、パッケージのマニフェスト ファイルの XML コードを変更することができます。 XML コードに対する変更は、パッケージのパッケージのマニフェスト ファイルにマージされます。  
  
#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>XML エディターを使用して、マニフェスト テンプレートを変更するには  
  
1.  **パッケージ デザイナー**、選択、**マニフェスト** タブで、展開、**オプションの編集**ノードを選択し、 **XML エディターで開いている**リンク。  
  
     XML への変更は、パッケージ マニフェスト ファイルにマージされます。  
  
#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>マニフェスト テンプレート ペインを使用して、マニフェスト テンプレートを変更するには  
  
1.  **パッケージ デザイナー**、選択、**マニフェスト** タブで、展開、**編集オプション**ノード、およびマニフェスト テンプレート ペインに表示される XML を変更します。  
  
     XML への変更に表示される、**プレビューのパッケージ化されたマニフェスト**ウィンドウ。  
  
## <a name="overwrite-the-packaged-manifest-file"></a>パッケージ マニフェスト ファイルを上書き  
 パッケージ デザイナーを無効にし、作成することができます、 *manifest.xml*ファイルを手動でします。 この手順を実行する最初に、パッケージ デザイナーの現在の設定は、パッケージのテンプレート XML ファイルに保存されます。 次に、変更したり、XML コードを上書きできます。  
  
> [!NOTE]  
>  追加パッケージ デザイナーが無効になっているときに、XML ファイルの SharePoint プロジェクト項目と機能を削除するか、これらのプロジェクト項目と機能がパッケージ化されません。  
  
#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>デザイナーを無効にして、パッケージ マニフェスト ファイルを上書きするには  
  
1.  **パッケージ デザイナー**、選択、**マニフェスト**タブ。  
  
2.  展開、**オプションの編集**ノード、選択、**上書き生成された XML と編集マニフェスト XML エディターで**リンクをクリックして、**はい**ボタン。  
  
     テンプレートは、現在のパッケージ マニフェスト ファイルで更新されます。  
  
## <a name="enable-the-package-designer"></a>パッケージ デザイナーを有効にします。  
 再度パッケージをカスタマイズするデザイナーが有効にすることができます、 *manifest.xml*ファイル。  
  
#### <a name="to-re-enable-the-designer"></a>デザイナーを再度有効にするには  
  
1.  **パッケージ デザイナー**、選択、**マニフェストの編集を破棄し、デザイナーを再度有効に**リンクをクリックして、**はい**ボタン。  
  
     元のテキストで、テンプレートが更新され、XML への変更は失われます。  
  
## <a name="see-also"></a>関連項目
 [パッケージ化し、SharePoint ソリューションのデプロイ](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
