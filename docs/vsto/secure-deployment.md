---
title: デプロイのセキュリティ保護します。
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
ms.openlocfilehash: 852e66bb4e29e732093cdac6b44c6791ad9b772d
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671081"
---
# <a name="secure-deployment"></a>デプロイのセキュリティ保護します。
  Office ソリューションを作成するときに実行するプロジェクトでコードを許可する、開発用コンピューターが自動的に更新されます。 ただし、ソリューションを配置するときに、ソリューションに証明書で署名するかを使用して、信頼の決定の基になる証拠を提供する必要があります、[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]信頼プロンプト キー。 詳細については、次を参照してください。 [Office ソリューションに信頼を付与](../vsto/granting-trust-to-office-solutions.md)します。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 ドキュメント レベルのカスタマイズに、ネットワークの場所にドキュメントを配置する場合、Office アプリケーションのセキュリティ センターで信頼できる場所の一覧にドキュメントの場所を追加する必要がありますもできます。 エンドユーザーのコンピューターにドキュメントのアクセス許可を設定する方法の詳細については、次を参照してください。[ドキュメントに信頼を付与](../vsto/granting-trust-to-documents.md)します。  
  
## <a name="prevent-office-solutions-from-running-code"></a>Office ソリューションがコードを実行するを防ぐ  
 管理者は、すべての Office ソリューションがコンピューターで実行されていることを防ぐために、レジストリを使用できます。 マネージ コード拡張機能を Office ソリューションが開かれた場合、Visual Studio Tools for Office ランタイム チェック エントリかどうか、名前の`Disabled`が存在するコンピューターで次のレジストリ キーのいずれかの。  
  
- **HKEY_CURRENT_USER\Software\Microsoft\VSTO**  
  
- **この**  
  
  Office ソリューションのコードの実行を防ぐために作成、`Disabled`一方または両方のこれらのレジストリ キーの下のエントリの値を次のデータ型のいずれかを指定して`Disabled`:  
  
- REG_SZ または REG_EXPAND_SZ「0」(ゼロ) 以外の任意の文字列に設定されています。  
  
- 0 (ゼロ) 以外の値に設定されている REG_DWORD です。  
  
  コードを実行する Office ソリューションを有効にするには、両方を設定、 `Disabled` 0 (ゼロ) へのエントリまたはレジストリ エントリを削除します。  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューションをデプロイします。](../vsto/deploying-an-office-solution.md)   
 [実行したり、Office ソリューションをホストするコンピューターを準備します。](https://msdn.microsoft.com/be1b173f-7261-4d74-aa4e-94ccd43db8d8)   
 [セキュリティで保護された Office ソリューション](../vsto/securing-office-solutions.md)  
  
  