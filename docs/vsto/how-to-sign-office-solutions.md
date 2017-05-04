---
title: "方法: Office ソリューションに署名する | Microsoft Docs"
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
  - "証明書 [Visual Studio での Office 開発], Office ソリューション"
  - "セキュリティ [Visual Studio での Office 開発], 署名 (Office ソリューションに)"
  - "署名 (マニフェストに) [Visual Studio での Office 開発]"
ms.assetid: d3df5ee6-f1b7-47ed-b7ee-8985679ee3af
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# 方法: Office ソリューションに署名する
  ソリューションに署名する場合は、証明書を証拠として使用し、ソリューションに信頼を付与することができます。  複数のソリューションに対して同じ証明書を使用できます。この場合、すべてのソリューションはセキュリティ ポリシーを更新することなく信頼されます。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 マニフェストの生成および編集ツール \(mage.exe および mageui.exe\) を使用してアプリケーション マニフェストと配置マニフェストを手動で編集する場合、これらのマニフェストを使用するには、事前にマニフェストに再署名することが必要です。  詳細については、「[方法: アプリケーション マニフェストおよび配置マニフェストに再署名する](../Topic/How%20to:%20Re-sign%20Application%20and%20Deployment%20Manifests.md)」を参照してください。  
  
## 証明書を使用した署名  
 証明書は 1 つのファイルで、一意のキーと、ソリューションの発行者の ID が格納されています。  証明書は、証明機関から購入するか、開発者自身の証明書を作成して証明機関の署名を受けます。  
  
 Visual Studio では、デバッグできるように、一時的な証明書を使用して Office ソリューションに署名します。  配置するソリューションでは、一時的な証明書を証拠としては使用しないでください。  
  
#### 証明書を使用して Office ソリューションに署名するには  
  
1.  **\[プロジェクト\]** メニューの **\[*SolutionName* のプロパティ\]** をクリックします。  
  
2.  **\[署名\]** タブをクリックします。  
  
3.  **\[ClickOnce マニフェストに署名する\]** を選択します。  
  
4.  **\[ストアから選択\]** または **\[ファイルから選択\]** をクリックして証明書を探し、証明書の位置まで移動します。  
  
5.  正しい証明書が使用されていることを確認するには、**\[詳細情報\]** をクリックし、証明書情報を表示します。  
  
## 参照  
 [Office ソリューションのセキュリティ保護](../vsto/securing-office-solutions.md)   
 [Office ソリューションへの信頼の付与](../vsto/granting-trust-to-office-solutions.md)   
 [ページ &#40;プロジェクト デザイナー&#41;](../ide/reference/signing-page-project-designer.md)  
  
  