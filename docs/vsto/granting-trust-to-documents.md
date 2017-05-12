---
title: "ドキュメントへの信頼の付与"
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
  - "付与 (信頼を) [Visual Studio での Office 開発]"
  - "信頼のリスト [Visual Studio での Office 開発], 信頼のリストの概要"
  - "セキュリティ [Visual Studio での Office 開発], 信頼"
  - "信頼 [Visual Studio での Office 開発], 2007 Office system"
ms.assetid: 16893647-501e-4836-98af-a79a1e9de3ee
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# ドキュメントへの信頼の付与
  ドキュメント レベルのプロジェクトでは、証明書を使用したマニフェストへの署名や、信頼プロンプトのクリックなど、アプリケーション レベルのプロジェクトと同じセキュリティ要件が適用されます。  また、ドキュメントまたはブックは、信頼できる場所として指定されたディレクトリに置く必要があります。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## 信頼できる場所  
 [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] のアプリケーションおよびOffice 2010 には、信頼できる場所などの、ユーザーがセキュリティとプライバシー設定を構成できるセキュリティ センターがあります。   Officeソリューションでは、ローカル コンピューターは信頼できる場所と見なされます。 ただし、ディレクトリの中には、リスクが高めであるために信頼できないものもあります \(システム、各ユーザー、Internet Explorer 用の一時フォルダーなど\)。  
  
 セキュリティ センターに関する詳細については、「[Office 2010 でのセキュリティー ポリシーと設定](http://go.microsoft.com/fwlink/?LinkId=89202)」を参照してください。  信頼できるフォルダーを作成、管理、削除、および構成する方法の詳細については、「[2007 Office system で信頼できる場所および信頼できる発行元の設定を構成する](http://go.microsoft.com/fwlink/?LinkId=89203)」および「[ファイルに対して信頼できる場所を作成、削除、変更する](https://support.office.com/ja-jp/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62)」を参照してください。  
  
## Office ソリューションに固有のセキュリティに関する考慮事項  
 どのフォルダーを信頼できる場所に追加するかを検討するときには、以下のセキュリティ上の問題に留意する必要があります。  
  
-   ローカル フォルダーは安全性が高いと見なされ、暗黙的に信頼されます。   ファイル共有などのリモートの場所は、信頼できる場所として指定する必要があります。  
  
-   信頼できる場所にディレクトリを追加すると、Office ソリューションだけでなく VBA コードおよび ActiveX コードにも完全な信頼が付与されます。  そのため、ルート ディレクトリやマイ ドキュメント フォルダーは信頼できる場所として指定しないでください。  
  
-   ドキュメント自体は信頼できる場所を使用することによって信頼されますが、カスタマイズを信頼するためには追加のアクセス許可が必要です。  カスタマイズに完全な信頼を付与するには、証明書を使用したマニフェストへの署名、信頼プロンプトのクリック、Office ソリューションの Program Files ディレクトリへのインストールのいずれかを行います。  
  
-   ドキュメント レベルのソリューションのドキュメントまたはブックは、アセンブリと同じディレクトリ、または別のディレクトリに保存できます。  たとえば、ドキュメントを SharePoint サーバー上に置き、アセンブリをネットワーク ファイル共有に置くことも可能です。  詳細については、「[方法: ClickOnce を使用して SharePoint Server にドキュメント レベルの Office ソリューションを公開する](http://msdn.microsoft.com/ja-jp/2408e809-fb78-42a1-9152-00afa1522e58)」を参照してください。  
  
## 参照  
 [Office ソリューションへの信頼の付与](../vsto/granting-trust-to-office-solutions.md)   
 [Office ソリューションのセキュリティのトラブルシューティング](../vsto/troubleshooting-office-solution-security.md)   
 [Office ソリューションのセキュリティ保護](../vsto/securing-office-solutions.md)  
  
  