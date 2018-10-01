---
title: コンポーネントの管理 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: be8a771c0f5de92664914f4f158db9054e321e19
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538518"
---
# <a name="component-management"></a>コンポーネント管理
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[コンポーネント管理](https://docs.microsoft.com/visualstudio/extensibility/internals/component-management)します。  
  
Windows インストーラーのタスクの単位は、Windows インストーラーのコンポーネント (WICs または単なるコンポーネントとも呼ばれます) と呼ばれます。 各 WIC では、インストールと Windows インストーラーの使用設定に対する参照カウントの基本的な単位を識別する GUID。  
  
 VSPackage、インストーラーを作成するいくつかの製品を使用できますが、この説明は Windows インストーラー (.msi) ファイルの使用を想定しています。 インストーラーを作成するときに、正しい参照カウントが常に発生するため、ファイルの配置正しく管理する必要があります。 その結果、製品の異なるバージョンに影響またはインストールの組み合わせで互いを中断してシナリオをアンインストールします。  
  
 Windows インストーラー、参照カウントは、コンポーネント レベルで発生します。 リソースの整理を慎重にする必要があります: ファイルやレジストリ エントリ、— コンポーネントにします。 組織の他のレベルがある-モジュール、機能、および製品など、さまざまなシナリオで役立つことができます。 詳細については、次を参照してください。 [Windows インストーラーの基本事項](../../extensibility/internals/windows-installer-basics.md)します。  
  
## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>サイド バイ サイドでインストールのセットアップの作成のガイドライン  
  
-   作成者のファイルとレジストリ キーを独自のコンポーネントのバージョン間で共有されます。  
  
     これにより、次のバージョンを簡単に使用することができます。 たとえば、グローバルに登録されているタイプ ライブラリ ファイルの拡張子、HKEY_CLASSES_ROOT、という具合に登録されているその他の項目。  
  
-   共有コンポーネントを別のマージ モジュールにグループ化します。  
  
     これは、正しくサイド - 今後の作成者が役立ちます。  
  
-   バージョン間で同じ Windows インストーラー コンポーネントを使用して共有ファイルおよびレジストリ キーをインストールします。  
  
     別のコンポーネントを使用する場合は、ファイルおよびレジストリ エントリはアンインストール 1 つのバージョン管理 VSPackage がアンインストールされますが、別の VSPackage がまだインストールされている場合。  
  
-   同じコンポーネントのバージョン管理と共有の項目を混在させないでください。  
  
     そうと、グローバルな場所と分離された場所にバージョン管理された項目を共有項目をインストールできなくなります。  
  
-   バージョン管理されたファイルをポイントする共有のレジストリ キーはありません。  
  
     この場合、別のバージョン管理 VSPackage のインストール時に共有キーが上書きされます。 2 番目のバージョンを削除した後、キーが指しているが、ファイルはなくなりました。  
  
## <a name="see-also"></a>関連項目  
 [共有およびバージョン管理 Vspackage の使い分け](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [VSPackage のセットアップ シナリオ](../../extensibility/internals/vspackage-setup-scenarios.md)

