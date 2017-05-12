---
title: "Information Rights Management とマネージ コード拡張機能の概要"
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
  - "ドキュメント [Visual Studio での Office 開発], 制限されたアクセス許可"
  - "Information Rights Management [Visual Studio での Office 開発]"
  - "IRM [Visual Studio での Office 開発]"
  - "Office ドキュメント [Visual Studio での Office 開発, 制限されたアクセス許可"
  - "権限管理 [Visual Studio での Office 開発]"
  - "ブック [Visual Studio での Office 開発], 制限されたアクセス許可"
ms.assetid: 9728f5fe-9122-48e7-b0a3-9f5e0a16164f
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Information Rights Management とマネージ コード拡張機能の概要
  Microsoft Office Word と Microsoft Office Excel は、Information Rights Management \(IRM\) という機能を備えています。これは、承認されていないユーザーによる機密情報の表示や変更を禁止する機能です。  Information Rights Management の機能の詳細については、それぞれの Office アプリケーションのヘルプを参照してください。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## アクセス許可が制限されたドキュメントの分離コードの実行  
 IRM を使用する文書またはブックがソリューションに含まれている場合、既定では、Word および Excel はコードの実行を許可しません。  文書の作成者であるか、フル コントロール アクセスを保持している場合は、ソリューションが動作するよう既定値を変更できます。  詳細については、「[方法 : アクセス許可が制限されたドキュメントでの分離コードの実行を許可する](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)」を参照してください。  
  
 IRM は、文書にキャッシュされたデータの取得や操作のために <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> が使用されないようにします。  
  
## マネージ コード拡張機能を使用するドキュメントに対するエンド ユーザーによるアクセス許可の制限  
 ソリューション内の文書やブックに対してフル コントロール アクセスを持つユーザーは、IRM を使用してアクセス許可を制限できます。  たとえば、経理部で、データベースのデータを基にワークシートを自動作成するソリューションを使用している場合、そのエンド ユーザーは、経理部のユーザーだけに変更アクセスを許可して、他の部署のユーザーには読み取りアクセスを許可できます。  ユーザーが制限付きアクセス許可を追加すると、既定では、ワークシートの分離コードが実行できなくなるため、ワークシートが自動生成されなくなります。  
  
 この問題を解決するには、ドキュメントやブックに対するフル コントロール アクセスを持つユーザーが、既定のアクセス許可設定を変更して、プログラムによるオブジェクト モデルへのアクセスを許可する必要があります。  詳細については、「[方法 : アクセス許可が制限されたドキュメントでの分離コードの実行を許可する](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)」を参照してください。  
  
## 参照  
 [ドキュメント レベルのソリューションにおけるドキュメントの保護](../vsto/document-protection-in-document-level-solutions.md)   
 [Office ドキュメントのパスワード保護](../vsto/password-protection-on-office-documents.md)   
 [Office ソリューションのセキュリティ保護](../vsto/securing-office-solutions.md)   
 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)   
 [Office ソリューションのデザインと作成](../vsto/designing-and-creating-office-solutions.md)  
  
  