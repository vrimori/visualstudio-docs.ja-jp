---
title: "方法: リボン デザイナーからリボン XML にエクスポート |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, XML
- customizing the Ribbon, XML
- Ribbon [Office development in Visual Studio], XML
- Ribbon [Office development in Visual Studio], exporting
- XML [Office development in Visual Studio], Ribbon
- Ribbon Designer [Office development in Visual Studio]
- exporting Ribbon
ms.assetid: 96e0e9ed-4392-4f45-ac33-b6f7c22ea321
caps.latest.revision: "37"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: d7cbdf38b3debd7710ed036d008d52b8ef080d37
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>方法 : リボンをリボン デザイナーからリボン XML にエクスポートする
  **リボン (ビジュアル デザイナー)**項目がリボンのカスタマイズのすべての種類をサポートしていません。 高度な方法でリボンをカスタマイズするには、リボンをデザイナーからリボン XML にエクスポートし、XML を直接編集します。  
  
> [!NOTE]  
>  リボン XML ファイルにないすべてのプロパティ値が表示されます。 詳細については、次を参照してください。[リボンの概要](../vsto/ribbon-overview.md)です。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>リボンをリボン デザイナーからリボン XML にエクスポートするには  
  
1.  リボン コード ファイルを右クリックして**ソリューション エクスプ ローラー**、クリックして**ビュー デザイナー**です。  
  
2.  リボン デザイナーを右クリックし、をクリックして**リボンを XML にエクスポート**です。  
  
     Visual Studio は、プロジェクトにリボン XML ファイルとリボン XML コード ファイルを追加します。  
  
3.  リボン コード クラスで始まるコメントを探します`TODO:`です。  
  
4.  これらのコメント内のコード ブロックのコピー、 **ThisAddin**、 **ThisWorkbook**、または**ThisDocument**クラスを開発しているソリューションの種類によって異なります。  
  
     このコードにより、Microsoft Office アプリケーションを検出して、カスタム リボンを読み込みます。 詳細については、「 [Ribbon XML](../vsto/ribbon-xml.md)」を参照してください。  
  
5.  **ThisAddin**、 **ThisWorkbook**、または**ThisDocument**クラス、コード ブロックのコメントを解除します。  
  
     コード コメントを解除すると後、次の例のようにします。 この例では、リボン クラスが呼び出されます`MyRibbon`です。  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
6.  リボン XML コード ファイルに切り替えるし、検索、`Ribbon Callbacks`領域。  
  
     これは、ボタンのクリックしてなどのユーザー アクションを処理するコールバック メソッドを記述します。  
  
7.  リボン デザイナー コードで記述したそれぞれのイベント ハンドラーのコールバック メソッドを作成します。  
  
8.  イベント ハンドラーからすべてのイベント ハンドラー コードをコールバック メソッドに移動し、リボン機能拡張 (RibbonX) プログラミング モデルを使用するコードを変更します。  
  
     コールバック メソッドの記述と RibbonX プログラミング モデルの使用については、次を参照してください。[リボン XML](../vsto/ribbon-xml.md)です。  
  
## <a name="see-also"></a>参照  
 [リボンの概要](../vsto/ribbon-overview.md)   
 [リボン デザイナー](../vsto/ribbon-designer.md)   
 [リボン XML](../vsto/ribbon-xml.md)   
 [チュートリアル: リボン デザイナーを使用してカスタム タブの作成](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [チュートリアル: リボン XML によるカスタム タブの作成](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  