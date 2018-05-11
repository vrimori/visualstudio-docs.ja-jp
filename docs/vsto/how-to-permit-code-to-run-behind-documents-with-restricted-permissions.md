---
title: '方法: アクセス許可の制限のドキュメントの背後に実行するようにコードを許可 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Information Rights Management [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- IRM [Office development in Visual Studio]
- code [Office development in Visual Studio], running behind restricted documents
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: eb5b9421bd6d0228a93ba7ba7516c9ebc7b7c761
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>方法 : アクセス許可が制限されたドキュメントでの分離コードの実行を許可する
  Microsoft Office の Information Rights Management (IRM) 機能を使用して、文書またはブックへのアクセス許可を制限することができます。 既定では、制限された Microsoft Office Word 文書または Microsoft Office Excel ブックのコードは実行できません。 既定値を変更するには、オブジェクト モデルにアクセスできる、マネージ コード拡張機能と、ソリューションが動作できるようにします。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 文書またはブックの作成者またはフル コントロール アクセス許可設定を変更できる必要があります。  
  
### <a name="to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>ドキュメントの背後にあるアクセス許可の制限を実行するコードを許可するには  
  
1.  Word または Excel の文書またはブックを開きます。  
  
2.  をクリックして、**ファイル** タブで、 をポイント**準備**、 をポイント**を制限するアクセス許可**、順にクリック**制限付きアクセス**です。  
  
    > [!NOTE]  
    >  初めて使用する場合は、Windows Rights Management クライアントのインストールに求められます。 クライアントをインストールした後は、同じ手順を繰り返す必要があります。  
  
3.  **権限**ダイアログ ボックスで、**この文書へのアクセスを制限する**、順にクリック**オプションより**です。  
  
4.  **ユーザーの追加権限****コンテンツをプログラムでアクセス**です。  
  
 Word または Excel オブジェクト モデルへのプログラムによるアクセスが許可されます。  
  
## <a name="see-also"></a>関連項目  
 [Information Rights Management とマネージ コード拡張機能の概要](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [ドキュメント レベルのソリューションでドキュメントの保護](../vsto/document-protection-in-document-level-solutions.md)   
 [Office ドキュメントのパスワード保護](../vsto/password-protection-on-office-documents.md)   
 [設計と、Office ソリューションの作成](../vsto/designing-and-creating-office-solutions.md)   
 [Office ソリューションのセキュリティ保護](../vsto/securing-office-solutions.md)   
 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)  
  
  