---
title: "Office ドキュメントのパスワード保護 |Microsoft ドキュメント"
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
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- passwords [Office development in Visual Studio], document protections
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
ms.assetid: 9cee99c8-73c6-4f89-9d5e-7912c876ff96
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 45f350fed3c806a9ac8f79178a50ef22aa0a800e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="password-protection-on-office-documents"></a>Office ドキュメントのパスワード保護
  パスワードを知らない人に開けませんできるように、Microsoft Office Word 文書と Microsoft Office Excel ブックでパスワードを設定することができます。 このオプションの名前は**[パスワード]**です。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 既存のドキュメントおよびいるブックを使用してドキュメント レベルのプロジェクトを作成する**[パスワード]**有効にします。 持つ Word および Excel のドキュメントの Visual Studio での動作が異なります**[パスワード]**有効にします。  
  
 有効化については**[パスワード]**、Word または Excel でのヘルプを参照してください。  
  
## <a name="behavior-of-excel-and-word"></a>Excel および Word の動作  
 Visual Studio で Excel ブックを開くたびに**[パスワード]**が有効な入力を求められたら、パスワードです。 ソリューションをビルドするときに求められます、パスワードをもう一度、ビルド時にドキュメントが開かれているためです。  
  
 最初に開く、Word 文書が Visual Studio で**[パスワード]**有効にすると、単語の入力を求め、パスワードです。 正常にパスワードを入力した後**[パスワード]**ドキュメントから削除し、ドキュメントを開いて、パスワードは必要なくなった。 ソリューションでドキュメントをする場合は、前にパスワードを要求するように開くことができる、有効にする必要があります**[パスワード]**最終的なビルドの後に、ソリューションを展開する前にします。  
  
## <a name="see-also"></a>関連項目  
 [ドキュメント レベルのソリューションでドキュメントの保護](../vsto/document-protection-in-document-level-solutions.md)   
 [Information Rights Management とマネージ コード拡張機能の概要](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [方法: アクセス許可の制限のドキュメントの背後に実行するようにコードを許可します。](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Office ソリューションのデザインと作成](../vsto/designing-and-creating-office-solutions.md)  
  
  