---
title: "セキュリティ保護された展開 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio], security
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- ClickOnce deployment [Office development in Visual Studio], security
ms.assetid: c5ba86b1-e87f-4508-8c5a-1295681a9590
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: cace0c9826a76a4a8341c6b85e1219dcf287e80a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="secure-deployment"></a>安全な配置
  Office ソリューションを作成すると、開発用コンピューターを実行するプロジェクトでコードを許可する自動的に更新されます。 ただし、ソリューションを配置するときは、ソリューションに、証明書で署名するかを使用して、信頼の決定を基になる証拠を提供する必要があります、[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]信頼プロンプト キー。 詳細については、次を参照してください。 [Office ソリューションへの信頼の付与](../vsto/granting-trust-to-office-solutions.md)です。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 ドキュメント レベルのカスタマイズに、ドキュメントをネットワークの場所に配置する場合、Office アプリケーションのセキュリティ センターで信頼できる場所の一覧にドキュメントの場所を追加する必要がありますもします。 コンピューターをエンドユーザーにドキュメントのアクセス許可を設定する方法の詳細については、次を参照してください。[ドキュメントへの信頼の付与](../vsto/granting-trust-to-documents.md)です。  
  
## <a name="preventing-office-solutions-from-running-code"></a>Office ソリューションのコードの実行を妨げてください。  
 管理者は、レジストリを使用して、すべての Office ソリューションをコンピューターで実行されないようにすることができます。 マネージ コード拡張機能を Office ソリューションを開いたときに、Office のランタイム チェックのための Visual Studio Tools エントリかどうか、名前を持つ`Disabled`が存在するコンピューターで次のレジストリ キーのいずれかの。  
  
-   `HKEY_CURRENT_USER\Software\Microsoft\VSTO`  
  
-   `HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO`  
  
 Office ソリューションを防ぐため、コードを実行してから、作成、`Disabled`いずれかまたは両方のレジストリ キー、下のエントリの次のデータ型と値のいずれかを指定して`Disabled`:  
  
-   REG_SZ または REG_EXPAND_SZ「0」(ゼロ) 以外の任意の文字列に設定されています。  
  
-   0 (ゼロ) 以外の値に設定する REG_DWORD です。  
  
 Office ソリューションのコードを実行するには、両方の設定、 `Disabled` 0 (ゼロ) にエントリまたはレジストリ エントリを削除します。  
  
## <a name="see-also"></a>参照  
 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)   
 [実行するか、Office ソリューションをホストするコンピューターを準備します。](http://msdn.microsoft.com/en-us/be1b173f-7261-4d74-aa4e-94ccd43db8d8)   
 [Office ソリューションのセキュリティ保護](../vsto/securing-office-solutions.md)  
  
  