---
title: "方法: サービスのデータに接続する | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "データ [Visual Studio], 接続 (Web サービスに)"
  - "データ [Visual Studio], 読み取り (Web サービスから)"
  - "データ ソース, 作成 (Web サービスから)"
  - "読み取り (データを), Web サービスから"
  - "Web サービス, データ ソースとして"
  - "Web サービス, 接続"
  - "Web サービス, 読み取り (データを)"
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
caps.latest.revision: 32
caps.handback.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 方法: サービスのデータに接続する
サービスから返されたデータにアプリケーションを接続するには、[データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png)を実行し、**\[データ ソースの種類を選択\]** ページの **\[サービス\]** をクリックします。  
  
 ウィザードを完了すると、プロジェクトにサービス参照が追加され、[ウィンドウ](../Topic/Data%20Sources%20Window.md)ですぐに使用できるようになります。  
  
> [!NOTE]
>  **\[データ ソース\]** ウィンドウに表示される項目は、サービスから返される情報に応じて異なります。  サービスによっては、**データ ソース構成ウィザード**でバインドできるオブジェクトを作成するための十分な情報を提供しないものもあります。  たとえば、サービスから型指定されていないデータセットが返される場合、ウィザードを完了しても **\[データ ソース\]** ウィンドウには項目が表示されません。  これは、型指定されていないデータセットからはスキーマが提供されず、したがってウィザードでデータ ソースを作成するための十分な情報が得られないためです。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### アプリケーションをサービスに接続するには  
  
1.  **\[データ\]** メニューの **\[新しいデータ ソースの追加\]** をクリックします。  
  
2.  **\[データ ソースの種類を選択\]** ページで **\[サービス\]** をクリックし、**\[次へ\]** をクリックします。  
  
3.  使用するサービスのアドレスを入力するか、**\[探索\]** をクリックして現在のソリューション内のサービスを検索し、**\[移動\]** をクリックします。  
  
4.  必要に応じて、既定値の代わりに新しい**名前空間**を入力できます。  
  
    > [!NOTE]
    >  **\[詳細設定\]** をクリックして [\[サービス参照の構成\] ダイアログ ボックス](../Topic/Configure%20Service%20Reference%20Dialog%20Box.md)を開きます。  
  
5.  **\[OK\]** をクリックして、プロジェクトにサービス参照を追加します。  
  
6.  **\[完了\]** をクリックします。  
  
     **\[データ ソース\]** ウィンドウにデータ ソースが追加されます。  
  
## 次の手順  
  
#### アプリケーションに機能を追加するには  
  
-   **\[データ ソース\]** ウィンドウ内の項目を選択し、フォームにドラッグして、バインド コントロールを作成します。  詳細については、「[Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)」を参照してください。  
  
## 参照  
 [チュートリアル: WCF Data Service への WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [チュートリアル: WCF Data Service への Silverlight コントロールのバインド](../Topic/Walkthrough:%20Binding%20Silverlight%20Controls%20to%20a%20WCF%20Data%20Service.md)   
 [Windows Communication Foundation Services and WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)