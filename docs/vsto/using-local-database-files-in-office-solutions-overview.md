---
title: "Office ソリューションにおけるローカル データベース使用の概要 | Microsoft Docs"
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
  - "データ [Visual Studio での Office 開発], local"
  - "ローカル データ [Visual Studio での Office 開発]"
  - "Office アプリケーション [Visual Studio での Office 開発], データ"
ms.assetid: 7a920e6b-f0c3-4a62-b5dd-02668a6177b6
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Office ソリューションにおけるローカル データベース使用の概要
  Officeソリューションにデータベース ファイル \(SQL Server Express \(.mdf\) ファイルやMicrosoft Office Access \(.mdb\) ファイルなどの含めることができます。  これにより、たとえば 1 つのコンピューターだけで使用されるローカルな在庫ソリューションのように、集中化されたデータベースの必要がない状況では、エンド ユーザーはローカル データベースを使用できます。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## プロジェクトへのデータベース ファイルのインポート  
 データベース ファイルをプロジェクトにインポートするには、**データ ソース構成**ウィザードを使用し、データベース ファイルに基づいてデータ ソースを作成します。  このウィザードでは、データベース ファイルと型指定されたデータセットをプロジェクトに追加します。  
  
## データベース ファイルの配置  
 **データ ソース構成ウィザード**では、相対パスに基づいてローカル データベース ファイルとの接続を作成します。  これにより、ローカル データベース ファイルの相対位置を維持する場合は、ソリューションを別のコンピューターへコピーすることができます。  
  
 ソリューションをサーバーに配置し、ドキュメントをエンド ユーザーに配布した場合、データベース ファイルを手動で配布し、ドキュメントへの相対位置が維持される場所にインストールする必要もあります。  つまり、エンド ユーザーは、データベース ファイルも一緒に移動しない限り、ドキュメントをコンピューター上の別の場所に移動できません。  
  
## ローカル データベース ファイルとデータセットのキャッシュ  
 Microsoft Office Excel および Microsoft Office Word 用のドキュメント レベルのソリューションでは、データセット インスタンスを <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 属性でマークすることにより、データセットをドキュメントにキャッシュできます。  **データ ソース構成**ウィザードを使用してデータベース ファイルをプロジェクトに追加すると、型指定されたデータセットが自動的にプロジェクトに追加されます。  データはユーザーのコンピューター上でローカルに使用できるので、このデータセットに <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> を適用する必要が生じることはほとんどありません。  詳細については、「[キャッシュされたデータ](../vsto/caching-data.md)」を参照してください。  
  
## 参照  
 [Office ソリューションでのコントロールへのデータのバインド](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [方法 : データベースからドキュメントにデータを読み込む](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [方法 : ホスト コントロールからのデータでデータ ソースを更新する](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)   
 [キャッシュされたデータ](../vsto/caching-data.md)  
  
  