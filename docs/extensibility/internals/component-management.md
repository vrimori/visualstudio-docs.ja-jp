---
title: "コンポーネントの管理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 398986499732a36819808b07f05f7d6b46787a94
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="component-management"></a>コンポーネントの管理
Windows インストーラーのタスクの単位は、Windows インストーラー コンポーネント (WICs またはだけコンポーネントとも呼ばれます) と呼ばれます。 インストールと Windows インストーラーを使用する設定に対する参照カウントの基本単位は、各 WIC を識別する GUID。  
  
 VSPackage のインストーラーを作成するいくつかの製品を使用できますが、ここには、Windows インストーラー (.msi) ファイルの使用が想定しています。 インストーラーを作成するときに常に、正しい参照カウントが行われるようにファイルの展開を正しく管理する必要があります。 その結果、製品のさまざまなバージョンは影響またはインストールのミックスで他の中断してシナリオをアンインストールします。  
  
 Windows インストーラーで、参照カウントは、コンポーネント レベルで発生します。 リソースの慎重に整理する必要があります: ファイル、レジストリ エントリ、およびなど — コンポーネントにします。 組織の他のレベルがある-モジュール、機能、および製品など — さまざまなシナリオで役立ちます。 詳細については、次を参照してください。 [Windows インストーラーの基本概念](../../extensibility/internals/windows-installer-basics.md)です。  
  
## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>サイド バイ サイド インストールのセットアップの作成のガイドライン  
  
-   作成者ファイルおよびレジストリ キーが独自のコンポーネントのバージョン間で共有されます。  
  
     これにより、簡単に次のバージョンで使用することができます。 たとえば、グローバルに登録されているタイプ ライブラリはファイル拡張子、HKEY_CLASSES_ROOT で登録されているその他の項目です。  
  
-   共有コンポーネントを別のマージ モジュールにグループ化します。  
  
     これは、サイド バイ サイド前進を正しくの作成者が役立ちます。  
  
-   異なるバージョン間で同じ Windows インストーラー コンポーネントを使用して、共有ファイルおよびレジストリ キーをインストールします。  
  
     別のコンポーネントを使用する場合は、ファイルおよびレジストリ エントリはアンインストール 1 つのバージョン管理された VSPackage がアンインストールされますが、別の VSPackage がまだインストールされているときにします。  
  
-   同じコンポーネント内のバージョン管理と共有項目を混在させないでください。  
  
     そうと、グローバルな場所と分離された場所にバージョン管理された項目に共有項目をインストールできなくなります。  
  
-   バージョン管理されたファイルをポイントする共有のレジストリ キーがありませんでした。  
  
     作成する場合は、別のバージョン管理された VSPackage をインストールすると、共有キーは上書きされます。 2 番目のバージョンを削除した後、キーが指してするファイルは失われます。  
  
## <a name="see-also"></a>参照  
 [共有とバージョン管理された Vspackage の使い分け](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [VSPackage のセットアップ シナリオ](../../extensibility/internals/vspackage-setup-scenarios.md)