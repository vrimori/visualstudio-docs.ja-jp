---
title: "信頼のリストによる Office ソリューションへの信頼の付与 | Microsoft Docs"
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
  - "アクセス許可 [Visual Studio での Office 開発]"
  - "信頼のリスト [Visual Studio での Office 開発]、信頼のリストの概要"
  - "セキュリティ [Visual Studio での Office 開発]、信頼のリスト"
  - "信頼のリスト [Visual Studio での Office 開発]"
ms.assetid: 6dae0128-435b-4fa1-aed9-73e728fdcacf
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# 信頼のリストによる Office ソリューションへの信頼の付与
  信頼のリストによって、ユーザーは発行者を識別する証明書で署名されている Office ソリューションに信頼を付与することができます。 信頼のリストはユーザー固有であり、ドキュメント レベルのカスタマイズと VSTO アドインに使用できます。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 ユーザーが信頼を付与されていない Office ソリューションを起動するとき、Microsoft Office ソリューションでは、[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 信頼プロンプトでその人にセキュリティ上の決定を求めます。 ユーザーがソリューションを信頼すると決定した場合、カスタマイズが実行され、次回からはプロンプトは出されません。  
  
## 信頼のリストと Windows インストーラー  
 Windows インストーラーを使用して Program Files ディレクトリに Office ソリューションをインストールする場合は、管理者権限が必要です。 Program Files ディレクトリに Office ソリューションがある場合、Office ソリューションに既にFullTrust アクセス許可が付与されているため、Visual Studio Tools for Office Runtime で信頼のリストがチェックされなくなります。  
  
## ClickOnce 信頼プロンプト  
 Office ソリューションに [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] の実装を使用すると、管理者は、プロンプトを許可するか、プロンプトを無効にするか、または信頼された証明書を要求するように、信頼プロンプト レベルを構成することができます。 この構成を行うには、信頼のリストへのアクセスを制御するレジストリ キーを使用します。  
  
 プロンプトを無効にすると、既知の信頼される証明書を持つソリューションのみをインストールすることができます。 プロンプト レベルのAuthenticode が必須に設定されている場合、ソリューションは既知の機関から証明書で署名を得る必要がありますが、信頼されたルート機関 \(信頼された証明書\) にチェーンする証明書は必要ありません。 プロンプトが許可されている場合、ソリューションは、ID が不明な証明書で署名することが可能になります。 このシナリオでは、信頼性に関する判断はエンド ユーザーまで持ち越されており、ソリューションのインストールには一時的な証明書で十分です。  
  
 詳細については、[ClickOnce 信頼された発行元の構成](http://go.microsoft.com/fwlink/?LinkId=94774)で「[方法: 信頼のリストのセキュリティを構成する](../vsto/how-to-configure-inclusion-list-security.md)」と表 2、プロンプト レベルのレジストリ キー値の起動時の効果を参照してください。  
  
## 信頼のリストの構造  
 有効な信頼のリストのエントリには、配置マニフェストへのパスと、ソリューションの署名に使用する公開キーという 2 つの部分があります。 ソリューションが信頼のリストに追加されると、信頼されているとみなされます。 Office ソリューションが実行されると、Office アプリケーションによって信頼リストのパブリックキーが配置マニフェストの署名キーと比較され、現在実行中のソリューションが元の信頼バージョンと同じであることが確認されます。  
  
## 参照  
 [Office ソリューションへの信頼の付与](../vsto/granting-trust-to-office-solutions.md)   
 [Office ソリューションのセキュリティ保護](../vsto/securing-office-solutions.md)  
  
  