---
title: "安全な配置 | Microsoft Docs"
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
  - "ClickOnce 配置 [Visual Studio での Office 開発], セキュリティ"
  - "配置 (アプリケーションを) [Visual Studio での Office 開発], セキュリティ"
  - "Office アプリケーション [Visual Studio での Office 開発], セキュリティ"
  - "Visual Studio での Office 開発, セキュリティ"
ms.assetid: c5ba86b1-e87f-4508-8c5a-1295681a9590
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# 安全な配置
  Office ソリューションを作成すると、開発コンピューターが自動的に更新され、プロジェクト内のコードの実行が許可されます。  ただし、ソリューションを配置するときには、証明書でソリューションに署名するか、[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 信頼プロンプト キーを使用して、信頼の決定の基礎となる証拠を提供する必要があります。  詳細については、「[Office ソリューションへの信頼の付与](../vsto/granting-trust-to-office-solutions.md)」を参照してください。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 ドキュメント レベルのカスタマイズでは、ドキュメントをネットワーク上に配置する場合、Office アプリケーションのセキュリティ センターで、そのドキュメントの場所を信頼できる場所の一覧に追加することも必要です。  エンド ユーザー コンピューターでドキュメントのアクセス許可を設定する方法の詳細については、「[ドキュメントへの信頼の付与](../vsto/granting-trust-to-documents.md)」を参照してください。  
  
## Office ソリューションでのコードの実行の防止  
 管理者はレジストリを使用して、すべての Office ソリューションがコンピューター上で実行されないようにできます。  マネージ コード拡張機能があるOfficeソリューションを開いた場合、名前 `Disabled` を持つエントリがコンピューターで次のレジストリ キーの数が1個あるかどうかをOfficeランタイム チェックのVisual Studio Tools:  
  
-   `HKEY_CURRENT_USER\Software\Microsoft\VSTO`  
  
-   `HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO`  
  
 Office ソリューションでコードを実行しないようにするには、上記のレジストリ キーのいずれかまたは両方の下に `Disabled` エントリを作成し、`Disabled` に対して次のいずれかのデータ型および値を指定します。  
  
-   REG\_SZ または REG\_EXPAND\_SZ。"0" \(ゼロ\) 以外の文字列に設定します。  
  
-   REG\_DWORD。0 \(ゼロ\) 以外の値に設定します。  
  
 Office ソリューションでコードを実行できるようにするには、両方の `Disabled` エントリを 0 \(ゼロ\) に設定するか、レジストリ エントリを削除します。  
  
## 参照  
 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)   
 [Office ソリューションを実行またはホストできるようにコンピューターを準備する](http://msdn.microsoft.com/ja-jp/be1b173f-7261-4d74-aa4e-94ccd43db8d8)   
 [Office ソリューションのセキュリティ保護](../vsto/securing-office-solutions.md)  
  
  