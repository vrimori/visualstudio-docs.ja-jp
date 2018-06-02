---
title: セキュリティで保護された展開
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio], security
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- ClickOnce deployment [Office development in Visual Studio], security
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 47cecda571a6826c2d7e845945c05d0264971134
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693332"
---
# <a name="secure-deployment"></a>セキュリティで保護された展開
  Office ソリューションを作成すると、開発用コンピューターを実行するプロジェクトでコードを許可する自動的に更新されます。 ただし、ソリューションを配置するときは、ソリューションに、証明書で署名するかを使用して、信頼の決定を基になる証拠を提供する必要があります、[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]信頼プロンプト キー。 詳細については、次を参照してください。 [Office ソリューションに信頼を付与](../vsto/granting-trust-to-office-solutions.md)です。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 ドキュメント レベルのカスタマイズに、ドキュメントをネットワークの場所に配置する場合、Office アプリケーションのセキュリティ センターで信頼できる場所の一覧にドキュメントの場所を追加する必要がありますもします。 コンピューターをエンドユーザーにドキュメントのアクセス許可を設定する方法の詳細については、次を参照してください。[ドキュメントへの信頼を付与](../vsto/granting-trust-to-documents.md)です。  
  
## <a name="prevent-office-solutions-from-running-code"></a>Office ソリューションがコードを実行するを防ぎます  
 管理者は、レジストリを使用して、すべての Office ソリューションをコンピューターで実行されないようにすることができます。 マネージ コード拡張機能を Office ソリューションを開いたときに、Office のランタイム チェックのための Visual Studio Tools エントリかどうか、名前を持つ`Disabled`が存在するコンピューターで次のレジストリ キーのいずれかの。  
  
-   **HKEY_CURRENT_USER\Software\Microsoft\VSTO**  
  
-   **この**  
  
 Office ソリューションを防ぐため、コードを実行してから、作成、`Disabled`いずれかまたは両方のレジストリ キー、下のエントリの次のデータ型と値のいずれかを指定して`Disabled`:  
  
-   REG_SZ または REG_EXPAND_SZ「0」(ゼロ) 以外の任意の文字列に設定されています。  
  
-   0 (ゼロ) 以外の値に設定する REG_DWORD です。  
  
 Office ソリューションのコードを実行するには、両方の設定、 `Disabled` 0 (ゼロ) にエントリまたはレジストリ エントリを削除します。  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューションを配置します。](../vsto/deploying-an-office-solution.md)   
 [実行するか、Office ソリューションをホストするコンピューターを準備します。](http://msdn.microsoft.com/en-us/be1b173f-7261-4d74-aa4e-94ccd43db8d8)   
 [セキュリティで保護された Office ソリューション](../vsto/securing-office-solutions.md)  
  
  