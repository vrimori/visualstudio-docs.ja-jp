---
title: "方法 : リボンをリボン デザイナーからリボン XML にエクスポートする"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "カスタム リボン, XML"
  - "カスタマイズ (リボンを), XML"
  - "エクスポート (リボンを)"
  - "リボン [Visual Studio での Office 開発], エクスポート"
  - "リボン [Visual Studio での Office 開発], XML"
  - "リボン デザイナー [Visual Studio での Office 開発]"
  - "XML [Visual Studio での Office 開発], リボン"
ms.assetid: 96e0e9ed-4392-4f45-ac33-b6f7c22ea321
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# 方法 : リボンをリボン デザイナーからリボン XML にエクスポートする
  **リボン \(ビジュアル デザイナー\)** 項目は、どのような種類のリボンのカスタマイズもサポートしていません。  高度な方法でリボンをカスタマイズするには、リボンをデザイナーからリボン XML にエクスポートし、XML を直接編集します。  
  
> [!NOTE]  
>  リボン XML ファイルには、すべてのプロパティ値が含まれるわけではありません。  詳細については、「[リボンの概要](../vsto/ribbon-overview.md)」を参照してください。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### リボンをリボン デザイナーからリボン XML にエクスポートするには  
  
1.  **ソリューション エクスプローラー**で、リボンのコード ファイルを右クリックし、**\[デザイナーの表示\]** をクリックします。  
  
2.  リボン デザイナーを右クリックし、**\[リボンを XML にエクスポート\]** をクリックします。  
  
     Visual Studio によってリボン XML ファイルおよびリボン XML コード ファイルがプロジェクトに追加されます。  
  
3.  リボン コード クラス内で、`TODO:.` で始まるコメントを探します。  
  
4.  それらのコメント内のコード ブロックを、開発するソリューションの種類に応じて、**ThisAddin**、**ThisWorkbook**、**ThisDocument** のいずれかのクラスにコピーします。  
  
     このコードによって、Microsoft Office アプリケーションはカスタム リボンを検出し、読み込むことができます。  詳細については、「[リボン XML](../vsto/ribbon-xml.md)」を参照してください。  
  
5.  **ThisAddin**、**ThisWorkbook**、**ThisDocument** のいずれかのクラスで、コード ブロックをコメントから外します。  
  
     コードをコメントから外すと、次の例のようになります。  この例では、リボン クラスの名前は `MyRibbon` です。  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/VB/ThisAddIn.vb#1)]  
  
6.  リボン XML コード ファイルに切り替え、`Ribbon Callbacks` 領域を探します。  
  
     この領域に、ボタンのクリックなどのユーザー アクションを処理するコールバック メソッドを記述します。  
  
7.  コールバック メソッドは、リボン デザイナー コードに記述した各イベント ハンドラーについて作成します。  
  
8.  すべてのイベント ハンドラー コードをイベント ハンドラーからコールバック メソッドに移動し、リボン機能拡張 \(RibbonX\) プログラミング モデルで動作するようにコードを変更します。  
  
     コールバック メソッドの作成と RibbonX プログラミング モデルの詳細については、「[リボン XML](../vsto/ribbon-xml.md)」を参照してください。  
  
## 参照  
 [リボンの概要](../vsto/ribbon-overview.md)   
 [リボン デザイナー](../vsto/ribbon-designer.md)   
 [リボン XML](../vsto/ribbon-xml.md)   
 [チュートリアル : リボン デザイナーを使用したカスタム タブの作成](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [チュートリアル : リボン XML によるカスタム タブの作成](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  