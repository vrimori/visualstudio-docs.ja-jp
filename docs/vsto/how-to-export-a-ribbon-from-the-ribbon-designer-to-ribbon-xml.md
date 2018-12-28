---
title: '方法: リボン デザイナーからリボン XML にエクスポートします。'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 370c2e1d08c47b8a5068d0227426d2b4083590a5
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53646933"
---
# <a name="how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>方法: リボン デザイナーからリボン XML にエクスポートします。
  **リボン (ビジュアル デザイナー)** 項目は、リボンのカスタマイズのすべての型をサポートしていません。 高度な方法でリボンをカスタマイズするには、リボンをデザイナーからリボン XML にエクスポートし、XML を直接編集します。  
  
> [!NOTE]  
>  リボン XML ファイルにすべてのプロパティ値が表示されます。 詳細については、次を参照してください。[リボンの概要](../vsto/ribbon-overview.md)します。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>リボン デザイナーからリボン XML にエクスポートするには  
  
1.  リボン コード ファイルを右クリックして**ソリューション エクスプ ローラー**、 をクリックし、**ビュー デザイナー**します。  
  
2.  リボン デザイナーを右クリックし、をクリックし、**リボンを XML にエクスポート**します。  
  
     Visual Studio では、リボン XML ファイルとリボン XML コード ファイルをプロジェクトに追加します。  
  
3.  リボン コード クラスで始まるコメントを探します`TODO:`します。  
  
4.  これらのコメントをコード ブロックをコピー、 **ThisAddin**、 **ThisWorkbook**、または**ThisDocument**開発しているソリューションの種類に応じて、クラスします。  
  
     このコードにより、Microsoft Office アプリケーションを検出して、カスタム リボンを読み込みます。 詳細については、「 [Ribbon XML](../vsto/ribbon-xml.md)」を参照してください。  
  
5.  **ThisAddin**、 **ThisWorkbook**、または**ThisDocument**クラス、コード ブロックをコメント解除します。  
  
     コードのコメントを解除した後は、次の例では、ようになります。 この例では、リボン クラスと呼びます`MyRibbon`します。  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
6.  リボン XML のコード ファイルにスイッチを見つけて、`Ribbon Callbacks`リージョン。  
  
     これは、ボタンのクリックしてなどのユーザー操作を処理するコールバック メソッドを記述します。  
  
7.  リボン デザイナー コードで記述した各イベント ハンドラーのコールバック メソッドを作成します。  
  
8.  コールバック メソッド、イベント ハンドラーからすべてのイベント ハンドラー コードを移動し、リボン機能拡張 (RibbonX) プログラミング モデルを使用するコードを変更します。  
  
     コールバック メソッドの記述と、RibbonX のプログラミング モデルを使用する方法については、次を参照してください。[リボン XML](../vsto/ribbon-xml.md)します。  
  
## <a name="see-also"></a>関連項目  
 [リボンの概要](../vsto/ribbon-overview.md)   
 [リボン デザイナー](../vsto/ribbon-designer.md)   
 [リボン XML](../vsto/ribbon-xml.md)   
 [チュートリアル: リボン デザイナーを使用してカスタム タブを作成します。](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [チュートリアル: リボン XML を使用してカスタム タブを作成します。](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  