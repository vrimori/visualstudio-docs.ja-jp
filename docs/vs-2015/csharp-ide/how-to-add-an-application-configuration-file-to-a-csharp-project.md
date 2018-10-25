---
title: '方法: c# プロジェクトに、アプリケーション構成ファイルの追加 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 43245704a2393b298f0f1d948d8a8829a4ef9bc4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49204790"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>方法: C# プロジェクトにアプリケーション構成ファイルを追加する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

アプリケーション構成ファイル (app.config ファイル) を C# プロジェクトに追加すると、共通言語ランタイムがアセンブリ ファイルを検索し読み込む方法をカスタマイズできます。 アプリケーション構成ファイルの詳細については、次を参照してください。[ランタイムがアセンブリを検索する方法](http://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34)します。  
  
> [!NOTE]
>  Windows ストアをサポートしていない<xref:System.Configuration>します。 その結果、ストア アプリには、app.config テンプレートが含まれていません。  
  
 プロジェクトをビルドするときに、開発環境は、app.config ファイルを自動的にコピー、実行可能ファイルと一致するコピーのファイル名を変更し、bin ディレクトリにコピーを移動します。  
  
### <a name="to-add-an-application-configuration-file-to-your-c-project"></a>C# プロジェクトに、アプリケーション構成ファイルを追加するには  
  
1.  メニュー バーで、**プロジェクト**、**新しい項目の追加**します。  
  
     **[新しい項目の追加]** ダイアログ ボックスが表示されます。  
  
2.  展開**インストール済み**、展開**Visual c# アイテム**を選択し、**アプリケーション構成ファイル**テンプレート。  
  
3.  **[名前]** ボックスに名前を入力し、**[追加]** ボタンをクリックします。  
  
     App.config はという名前のファイルは、プロジェクトに追加されます。  
  
## <a name="see-also"></a>関連項目  
 [アプリケーションの設定の管理 (.NET)](../ide/managing-application-settings-dotnet.md)   
 [構成ファイル スキーマ](http://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38)   
 [アプリの構成](http://msdn.microsoft.com/library/86bd26d3-737e-4484-9782-19b17f34cd1f)   
 [方法: .NET Framework のバージョンを対象とするアプリの構成](http://msdn.microsoft.com/en-us/5247b307-89ca-417b-8dd0-e8f9bd2f4717)   
 [Visual C# 開発環境の使用](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)