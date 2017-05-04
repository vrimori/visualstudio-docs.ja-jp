---
title: "Office ソリューションの共同開発 | Microsoft Docs"
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
  - "共同開発 [Visual Studio での Office 開発]"
  - "Office アプリケーション [Visual Studio での Office 開発], 共同開発"
  - "Visual Studio での Office 開発, 共同"
  - "ソース管理 [Visual Studio での Office 開発]"
ms.assetid: c493354b-17d3-4e50-85f0-968b104bc978
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Office ソリューションの共同開発
  Office プロジェクトでは、他の Visual Studio プロジェクトの場合と同じように、複数の開発者が共同で作業できます。  Visual Studio は、Microsoft Office が別の場所にインストールされていても、各コンピューターでその場所を正しく認識できます。  ただし、注意を必要とする重要な考慮事項もあります。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## デバッグ プロパティは共有されない  
 デバッグ プロパティは、ソース管理で複数のユーザー間では共有されません。  Visual Basic プロジェクトや Visual C\# プロジェクトでは、デバッグ プロパティはユーザー固有のファイル \(*ProjectName*.vbproj.user または *ProjectName*.csproj.user\) に格納されます。このファイルはソース管理で管理されません。  複数のユーザーがデバッグを実行する場合は、各自が手動でデバッグ プロパティを入力する必要があります。  
  
 プロジェクトがソース管理ではなくネットワーク共有にある場合は、共同開発者がソリューションを開いてアセンブリをテストできるようにするために、追加の手順が必要です。  
  
## ソース管理ではすべてのファイルのチェックアウトが必要  
 プロジェクトでソース管理を使用する場合、コード ファイルを変更するたびに、**ソリューション エクスプローラー**でそのコード ファイルの下位にあるファイルを \(既定では非表示のものも含めて\) すべてチェックアウトする必要があります。  最上位のコード ファイルのみをチェックアウトすると、変更が失われることがあります。  
  
 変更を加えた後で、すべてのファイルを再度チェックインします。  プロジェクトの非表示のコード ファイルに関する詳細については、「[Visual Studio 環境における Office プロジェクト](../vsto/office-projects-in-the-visual-studio-environment.md)」を参照してください。  
  
## ネットワーク上の共同作業のセキュリティ  
 ネットワーク場所 \(\\\\*Servername*\\*Sharename* など\) にあるドキュメント レベルのソリューションでは、作業している Microsoft Office アプリケーションの信頼できるフォルダーのリストに完全修飾位置を追加する必要があります。  メイン フォルダーの下位にあるサブディレクトリを含めるようにオプションを選択するか、デバッグ用のフォルダーとビルド用のフォルダーを信頼できるフォルダーのリストに具体的に追加します。  この方法の詳細については、「[ドキュメントへの信頼の付与](../vsto/granting-trust-to-documents.md)」を参照してください。  
  
 ビルド時に自動的に生成される一時的な証明書は、パスワードで保護されていません。  この証明書には、開発者のログイン名などの個人情報が含まれています。  一時的な証明書で署名したカスタマイズを配置すると、他のユーザーがこの情報にアクセスできる可能性があります。  
  
## 参照  
 [Office ソリューションのセキュリティ保護](../vsto/securing-office-solutions.md)   
 [Office ソリューションのデザインと作成](../vsto/designing-and-creating-office-solutions.md)   
 [Office ソリューションのビルド](../vsto/building-office-solutions.md)  
  
  