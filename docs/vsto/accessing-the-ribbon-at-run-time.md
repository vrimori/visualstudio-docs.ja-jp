---
title: "実行時のリボンへのアクセス | Microsoft Docs"
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
  - "Globals クラス, リボン"
  - "リボン [Visual Studio での Office 開発], アクセス"
  - "RibbonManager クラス"
ms.assetid: 8a7c7c6d-1a18-4d6b-98ee-e483d41f0cd8
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# 実行時のリボンへのアクセス
  リボンを表示、非表示、変更するコードを作成し、ユーザーがカスタム作業ウィンドウ、アクション ウィンドウ、または Outlook フォーム領域のコントロールからそのコードを実行できるようにすることができます。  
  
 リボンには、`Globals` クラスを使用してアクセスできます。  Outlook プロジェクトの場合は、特定の Outlook インスペクター ウィンドウまたは Outlook エクスプ ローラー ウィンドウに表示されるリボンにアクセスできます。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## Globals クラスを使用したリボンへのアクセス  
 `Globals` クラスを使用して、プロジェクトのどこからでもドキュメント レベルのプロジェクトまたは VSTO アドイン プロジェクトのリボンにアクセスできます。  
  
 `Globals` クラスの詳細については、「[Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)」を参照してください。  
  
 次の例では、`Globals` クラスを使用して `Ribbon1` という名前のカスタム リボンにアクセスし、リボンのコンボ ボックスに表示されるテキストを `Hello World` に設定します。  
  
 [!code-csharp[Trin_Outlook_FR_Access#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#4)]
 [!code-vb[Trin_Outlook_FR_Access#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#4)]  
  
## 特定の Outlook インスペクター ウィンドウに表示されるリボンのコレクションへのアクセス  
 Outlook *インスペクター*に表示されるリボンのコレクションにアクセスできます。  インスペクターは、ユーザーが電子メール メッセージを作成するなど、特定のタスクを実行するときに、Outlook で開かれるウィンドウです。  インスペクター ウィンドウのリボンにアクセスするには、`Globals` クラスの `Ribbons` プロパティを呼び出し、インスペクターを表す <xref:Microsoft.Office.Interop.Outlook.Inspector> オブジェクトを渡します。  
  
 次の例では、現在フォーカスがあるインスペクターのリボン コレクションを取得します。  この例では次に、`Ribbon1` という名前のリボンにアクセスして、リボンのコンボ ボックスに表示されるテキストを `Hello World` に設定します。  
  
 [!code-csharp[Trin_Outlook_FR_Access#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#5)]
 [!code-vb[Trin_Outlook_FR_Access#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#5)]  
  
## 特定の Outlook エクスプローラーで表示されるリボンのコレクションへのアクセス  
 Outlook *エクスプローラー*に表示されるリボンのコレクションにアクセスできます。  エクスプ ローラーは、Outlook のインスタンスの主要なアプリケーション ユーザー インターフェイス \(UI\) です。  エクスプローラー ウィンドウのリボンにアクセスするには、`Globals` クラスの `Ribbons` プロパティを呼び出し、エクスプローラーを表す <xref:Microsoft.Office.Interop.Outlook.Explorer> オブジェクトを渡します。  
  
 次の例では、現在フォーカスがあるエクスプローラーのリボン コレクションを取得します。  この例では次に、`Ribbon1` という名前のリボンにアクセスして、リボンのコンボ ボックスに表示されるテキストを `Hello World` に設定します。  
  
 [!code-csharp[Trin_Outlook_FR_Access#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#6)]
 [!code-vb[Trin_Outlook_FR_Access#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#6)]  
  
## 参照  
 [リボンの概要](../vsto/ribbon-overview.md)   
 [リボン デザイナー](../vsto/ribbon-designer.md)   
 [リボン XML](../vsto/ribbon-xml.md)   
 [リボン オブジェクト モデルの概要](../vsto/ribbon-object-model-overview.md)   
 [チュートリアル : リボン デザイナーを使用したカスタム タブの作成](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [チュートリアル : 実行時のリボン コントロールの更新](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Outlook のリボンのカスタマイズ](../vsto/customizing-a-ribbon-for-outlook.md)   
 [実行時におけるフォーム領域へのアクセス](../vsto/accessing-a-form-region-at-run-time.md)  
  
  