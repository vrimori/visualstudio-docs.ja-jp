---
title: "チュートリアル: カスタム エディターの作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9e8ea75cb96b36f885a55cbf9f174394379dc05a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-custom-editor"></a>チュートリアル: カスタム エディターの作成
VSPackage プロジェクト テンプレートは、C++ では、単純なカスタム エディターを作成できます。  VSPackage プロジェクト テンプレートには、c# または Visual Basic のプロジェクトがサポートされていません。 詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルに従うには、Visual Studio SDK をインストールする必要があります。 詳細については、次を参照してください。 [、Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。  
  
## <a name="the-visual-studio-package-project-template"></a>Visual Studio パッケージ プロジェクト テンプレート  
 Visual Studio パッケージ プロジェクト テンプレートは含まれて、**新しいプロジェクト**C++ の拡張機能フォルダーのダイアログ  
  
### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Visual Studio パッケージ テンプレートを使用して VSPackage を作成するには  
  
1.  Visual Studio パッケージ テンプレートを使用して、プロジェクトを作成します。  
  
2.  選択、**カスタム エディター**オプションをクリックして**次**です。 **エディター オプション**ページが表示されます。  
  
3.  エディターの名前を入力、**エディター名**ボックス。 エディターに関連付けたいファイル拡張子を入力、**ファイル拡張子**ボックス。 エディターはこの拡張子を持つファイルに対して使用できます。 ファイルの拡張子が登録 Visual Studio のみ、Windows ではなくされます。 エディターを使用して作成された新しいドキュメントの既定のファイル名を入力、**既定のファイル名**ボックス。  
  
4.  **[完了]** をクリックして、指定したフォルダーに VSPackage を作成します。  
  
### <a name="to-test-your-custom-editor"></a>カスタム エディターをテストするには  
  
1.  **ファイル** メニューのをポイント**新規** をクリックし、**ファイル**です。  
  
2.  **インストールされたテンプレート**のペイン、**新しいファイル** ダイアログ ボックスで、選択し、ファイル テンプレート、ファイルの種類を登録します。  
  
3.  をクリックして**開く**ドキュメントを表示および編集します。  
  
     エディターには、切り取りと貼り付け、検索と置換、および開く-読み込み操作がサポートしています。  
  
## <a name="see-also"></a>参照  
 [VSPackage](../extensibility/internals/vspackages.md)