---
title: "How to: Add, Update, or Remove a WCF Data Service Reference | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "service references [Visual Studio]"
  - "WCF Data Service reference"
  - "WCF data service references"
  - "ADO.NET service references"
  - "ADO.NET Data Service reference"
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Add, Update, or Remove a WCF Data Service Reference
*サービス参照*を使用すると、プロジェクトで 1 つ以上の [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] にアクセスできます。  [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] を検索するには、**\[サービス参照の追加\]** ダイアログ ボックスを使用します。ローカル エリア ネットワーク上にある現在のソリューションのサービスをローカルで検索することも、インターネット上のサービスを検索することもできます。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## サービス参照の追加  
  
#### 外部サービスへの参照を追加するには  
  
1.  **ソリューション エクスプローラー**で、サービスを追加するプロジェクトの名前を右クリックし、**\[サービス参照の追加\]** をクリックします。  
  
     **\[サービス参照の追加\]** ダイアログ ボックスが表示されます。  
  
2.  **\[アドレス\]** ボックスにサービスの URL を入力し、**\[移動\]** をクリックしてサービスを検索します。  サービスにユーザー名とパスワードによるセキュリティが実装されている場合は、ユーザー名とパスワードの入力を求められることがあります。  
  
    > [!NOTE]
    >  参照するのは、信頼できる送信元からのサービスのみにしてください。  信頼関係のないソースからの参照を追加すると、セキュリティが損なわれる場合があります。  
  
     前回有効なサービス メタデータが見つかった 15 件の URL を含む **\[アドレス\]** リストから、URL を選択することもできます。  
  
     検索の実行中はプログレス バーが表示されます。  **\[停止\]**をクリックすると、検索をいつでも停止できます。  
  
3.  **\[サービス\]** ボックスで、使用するサービスのノードを展開し、エンティティ セットを選択します。  
  
4.  **\[名前空間\]** ボックスで、参照に使用する名前空間を入力します。  
  
5.  **\[OK\]** をクリックして、プロジェクトに参照を追加します。  
  
     サービス クライアント \(プロキシ\) が生成され、サービスを記述したメタデータが app.config ファイルに追加されます。  
  
#### 現在のソリューションのサービスへの参照を追加するには  
  
1.  **ソリューション エクスプローラー**で、サービスを追加するプロジェクトの名前を右クリックし、**\[サービス参照の追加\]** をクリックします。  
  
     **\[サービス参照の追加\]** ダイアログ ボックスが表示されます。  
  
2.  **\[探索\]** をクリックします。  
  
     **\[サービス\]** ボックスに、現在のソリューションに含まれるすべてのサービス \([!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] および WCF サービス\) が追加されます。  
  
3.  **\[サービス\]** ボックスで、使用するサービスのノードを展開し、エンティティ セットを選択します。  
  
4.  **\[名前空間\]** ボックスで、参照に使用する名前空間を入力します。  
  
5.  **\[OK\]** をクリックして、プロジェクトに参照を追加します。  
  
     サービス クライアント \(プロキシ\) が生成され、サービスを記述したメタデータが app.config ファイルに追加されます。  
  
## サービス参照の更新  
 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] の Entity Data Model は変更されることがあります。  そのような場合は、サービス参照を更新する必要があります。  
  
#### サービス参照を更新するには  
  
-   **ソリューション エクスプローラー**で、サービス参照を右クリックし、**\[サービス参照の更新\]** をクリックします。  
  
     参照が元の場所から更新されている間、プログレス ダイアログ ボックスが表示され、メタデータの変更を反映してサービス クライアントが再生成されます。  
  
## サービス参照の削除  
 サービス参照が使用されなくなった場合は、ソリューションから削除できます。  
  
#### サービス参照を削除するには  
  
-   **ソリューション エクスプローラー**で、サービス参照を右クリックし、**\[削除\]** をクリックします。  
  
     ソリューションからサービス クライアントが削除され、サービスを記述したメタデータが app.config ファイルから削除されます。  
  
    > [!NOTE]
    >  サービス参照を参照するコードがある場合は、手動で削除する必要があります。  
  
## 参照  
 [Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md)