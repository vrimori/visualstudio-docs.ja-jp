---
title: Office ソリューションの共同開発
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], collaborative development
- Office development in Visual Studio, collaboration
- source control [Office development in Visual Studio]
- collaborative development [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9b4d22c92bd180eb27f8ebb50e65b24d17a92e47
ms.sourcegitcommit: a715de2ba8c703f37aa2102567b1aa2c0f05a117
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2018
ms.locfileid: "53441549"
---
# <a name="collaborative-development-of-office-solutions"></a>Office ソリューションの共同開発
  複数の開発者は、他の Visual Studio プロジェクトが共同作業と同じ方法で Office プロジェクトで作業できます。 Visual Studio では、別の場所で Office がインストールされている場合でも、各コンピューターに Microsoft Office のインストールが正常で検索します。 ただし、注意すべき重要な考慮事項があります。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="debug-properties-are-not-shared"></a>デバッグ プロパティは共有されません。  
 デバッグ プロパティは、ソース管理で複数のユーザー間では共有されません。 Visual Basic および Visual c# プロジェクトでは、ユーザー固有のファイルのデバッグ プロパティを格納 (*ProjectName*. vbproj.user または*ProjectName*。 csproj.user)、このファイルはソース管理されません。 複数のユーザーがデバッグを実行する場合は、各自が手動でデバッグ プロパティを入力する必要があります。  
  
 プロジェクトは、ソース管理ではなく、ネットワーク共有に格納されているが場合、ソリューションを開き、アセンブリをテストする共同開発者を有効にする追加の手順を実行する必要があります。  
  
## <a name="source-control-requires-checking-out-all-files"></a>ソース管理では、すべてのファイルをチェック アウトが必要です。  
 プロジェクトをソース管理を使用する場合、これをチェック アウトのすべてのファイル内のコード ファイルでする必要があります**ソリューション エクスプ ローラー** (など、 *ThisDocument*、 *ThisWorkbook*、または*ThisAddIn*コード ファイル)、コード ファイルを変更するたびにもファイルを既定では表示されません。 最上位のコード ファイルのみをチェックする場合、変更は失われます。  
  
 変更を行った後でバックアップのすべてのファイルを確認してください。 プロジェクト内の非表示コード ファイルの詳細については、次を参照してください。 [Visual Studio 環境における Office プロジェクト](../vsto/office-projects-in-the-visual-studio-environment.md)します。  
  
## <a name="security-for-informal-collaboration-on-a-network"></a>ネットワーク上の共同のセキュリティ  
 ネットワークの場所にあるすべてのドキュメント レベルのソリューションの (など\\ \\ *Servername*\\*Sharename*)、完全修飾の場所に追加する必要があります使用している Microsoft Office アプリケーションで信頼できるフォルダーの一覧。 メイン フォルダーの下のサブディレクトリを含める、または具体的にはデバッグを追加し、フォルダーを信頼できるフォルダーのリストをビルドするオプションを選択します。 これを行う方法の詳細については、次を参照してください。[ドキュメントに信頼を付与](../vsto/granting-trust-to-documents.md)します。  
  
 ビルド時に自動的に生成される一時的な証明書は、パスワードで保護されていません。 証明書には、開発者のログイン名と他の個人情報が含まれています。 一時的な証明書によって署名されているカスタマイズを配置する場合は、この情報にアクセスできない他のユーザー必要があります。  
  
## <a name="see-also"></a>関連項目  
 [セキュリティで保護された Office ソリューション](../vsto/securing-office-solutions.md)   
 [設計および Office ソリューションの作成](../vsto/designing-and-creating-office-solutions.md)   
 [Office ソリューションを構築します。](../vsto/building-office-solutions.md)  
  
  