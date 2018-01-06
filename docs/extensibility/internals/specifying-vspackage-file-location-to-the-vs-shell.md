---
title: "VS Shell VSPackage のファイルの場所を指定する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 35bd935683f8ace47536389ebc65f34311e9fcfd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>VS Shell VSPackage のファイルの場所を指定します。
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]アセンブリを VSPackage を読み込む DLL を検索できる必要があります。 特定できる、さまざまな方法で次の表で説明します。  
  
|メソッド|説明|  
|------------|-----------------|  
|コードベースのレジストリ キーを使用します。|送信するために、コードベースのキーを使用できます[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]任意のファイルの絶対パスから、VSPackage アセンブリを読み込めません。 キーの値は、DLL へのファイル パスにする必要があります。 これが最善の方法は、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]パッケージのアセンブリを読み込みます。 この手法は「コードベース/プライベート インストール ディレクトリ方法」と呼ばれることがあります。 登録時に、コードベースの値に渡される登録属性クラスのインスタンスを通じて、<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext>型です。|  
|DLL を置く、 **PrivateAssemblies**ディレクトリ。|内のアセンブリを配置、 **PrivateAssemblies**のサブディレクトリ、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ディレクトリ。 アセンブリに配置**PrivateAssemblies**は自動的に検出しますに表示されない、**参照の追加** ダイアログ ボックス。 間の違い**PrivateAssemblies**と**PublicAssemblies**はアセンブリで**PublicAssemblies**で列挙、**参照の追加**  ダイアログ ボックス。 "コードベース/プライベート installation directory"手法を使用しないように選択したかどうかをインストールする必要があります、 **PrivateAssemblies**ディレクトリ。|  
|厳密な名前のアセンブリとアセンブリのレジストリ キーを使用します。|アセンブリ キーは、明示的に指示するために使用できます[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]を読み込む、厳密な名前の VSPackage アセンブリ。 キーの値は、アセンブリの厳密な名前にする必要があります。|  
|DLL を置く、 **PublicAssemblies**ディレクトリ。|最後に、アセンブリもに配置できる、 **PublicAssemblies**サブディレクトリです。 アセンブリに配置**PublicAssemblies**は自動的に検出されにも表示されます、**参照の追加** ダイアログ ボックスで[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。<br /><br /> VSPackage アセンブリは、だけに置く必要があります、 **PublicAssemblies**ディレクトリが含まれている場合に、他の VSPackage 開発者が再利用するためのものでは、コンポーネントが管理されています。 アセンブリの大部分は、この条件を満たしていません。|  
  
> [!NOTE]
>  すべての依存アセンブリの厳密な名前の符号付きのアセンブリを使用します。 これらのアセンブリは、独自のディレクトリまたはグローバル アセンブリ キャッシュ (GAC) にもインストールする必要があります。 これを防ぎ、同じ基本ファイル名を持つ、厳密名のバインドと呼ばれるアセンブリと競合しています。