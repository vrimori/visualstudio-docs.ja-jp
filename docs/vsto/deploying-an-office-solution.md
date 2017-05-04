---
title: "Office ソリューションの配置 | Microsoft Docs"
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
  - "ClickOnce 配置 [Visual Studio での Office 開発], ClickOnce ソリューション配置の概要"
  - "ClickOnce 配置 [Visual Studio での Office 開発], イベント ビューアー"
  - "ClickOnce 配置 [Visual Studio での Office 開発], トラブルシューティング"
  - "配置 (アプリケーションを) [Visual Studio での Office 開発], イベント ビューアー"
  - "配置 (アプリケーションを) [Visual Studio での Office 開発], Office ソリューション (2007 system)"
  - "配置 (アプリケーションを) [Visual Studio での Office 開発], トラブルシューティング"
  - "Office アプリケーション [Visual Studio での Office 開発], Office ソリューションの配置"
  - "Visual Studio での Office 開発, Office ソリューションの配置"
  - "Visual Studio での Office 開発, イベント ビューアー"
  - "Visual Studio での Office 開発, トラブルシューティング"
  - "Office ソリューション [Visual Studio での Office 開発], 配置"
  - "ソリューション [Visual Studio での Office 開発], 配置 (Office ソリューションを) (2007 system)"
ms.assetid: 4cdf4bc6-72c5-4166-8019-d5fd61281079
caps.latest.revision: 78
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 74
---
# Office ソリューションの配置
  ClickOnce または Windows インストーラーを使用して、Office ソリューションを配置できます。  ClickOnce を使用すると、ソリューションを配置および更新するために必要な手順の数を減らすことができます。  Windows インストーラーを使用する場合は、ユーザーがソリューションをインストールする際に、ソリューションをどのようにインストールするか、およびセットアップ プログラムがどのページを表示するかを制御できます。  
  
## ClickOnce を使用したソリューションの配置  
 ClickOnce を使用してソリューションを配置するときは、ユーザーがインストールして実行できる中央の場所にソリューションを発行します。  新しいセットアップ プログラムをユーザーに配布しなくても、ソリューションを更新できます。この配置オプションの方が簡単ですが、ユーザーにカスタム設定ページを表示できません。  また、複数のユーザーがいるコンピューターでは、ソリューションを複数回インストールする必要があります。  「[ClickOnce を使用した Office ソリューションの配置](../vsto/deploying-an-office-solution-by-using-clickonce.md)」を参照してください。  
  
## Windows インストーラーを使用したソリューションの配置  
 Windows インストーラーを使用してソリューションを配置するときは、ユーザーにセットアップ プログラムを配布し、ユーザーがそのプログラムを使用してソリューションをインストールします。  セットアップ プログラムを使用すると、現在のユーザーのみではなく、コンピューターのすべてのユーザーに同時にソリューションをインストールできます。  また、ユーザーがソリューションをインストールするときに表示されるオプションを、少し詳細に制御できます。  たとえば、使用許諾契約を表示したり、ユーザーがソリューションの特定のコンポーネントをインストールできるようにしたりすることができます。  ただし、ソリューションを更新する場合は、新しいセットアップ プログラムを配布する必要があります。  「[Windows インストーラーを使用した Office ソリューションの配置](../vsto/deploying-an-office-solution-by-using-windows-installer.md)」を参照してください。  
  
## 参照  
 [Office ソリューションのセキュリティ保護](../vsto/securing-office-solutions.md)   
 [ClickOnce を使用した Office ソリューションの配置](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Windows インストーラーを使用した Office ソリューションの配置](../vsto/deploying-an-office-solution-by-using-windows-installer.md)   
 [Office ソリューション配置のトラブルシューティング](../vsto/troubleshooting-office-solution-deployment.md)  
  
  