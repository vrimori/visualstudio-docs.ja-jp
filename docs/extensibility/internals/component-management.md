---
title: コンポーネントの管理 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 31508fd720d1bf6695d6f735e57a829b72087ba9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53917451"
---
# <a name="component-management"></a>コンポーネントの管理
Windows インストーラーのタスクの単位は、Windows インストーラーのコンポーネント (WICs または単なるコンポーネントとも呼ばれます) と呼ばれます。 各 WIC では、インストールと Windows インストーラーの使用設定に対する参照カウントの基本的な単位を識別する GUID。  
  
 VSPackage、インストーラーを作成するいくつかの製品を使用できますが、この説明が Windows インストーラーの使用を前提としています (*.msi*) ファイル。 インストーラーを作成するときに、正しい参照カウントが常に発生するため、ファイルの配置正しく管理する必要があります。 その結果、製品の異なるバージョンに影響またはインストールの組み合わせで互いを中断してシナリオをアンインストールします。  
  
 Windows インストーラー、参照カウントは、コンポーネント レベルで発生します。 リソースの整理を慎重にする必要があります: ファイルやレジストリ エントリ、— コンポーネントにします。 組織の他のレベルがある-モジュール、機能、および製品など、さまざまなシナリオで役立つことができます。 詳細については、次を参照してください。 [Windows インストーラーの基本事項](../../extensibility/internals/windows-installer-basics.md)します。  
  
## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>サイド バイ サイドでインストールのセットアップの作成のガイドライン  
  
-   作成者のファイルとレジストリ キーを独自のコンポーネントのバージョン間で共有されます。  
  
     これにより次のバージョンでこれらを簡単に使用することができます。 たとえば、グローバルに登録されているタイプ ライブラリ ファイルの拡張子に登録されているその他のアイテム**HKEY_CLASSES_ROOT**など。  
  
-   共有コンポーネントを別のマージ モジュールにグループ化します。  
  
     この戦略では、今後はサイド バイ サイドでインストールを正しく作成するのに役立ちます。  
  
-   バージョン間で同じ Windows インストーラー コンポーネントを使用して共有ファイルおよびレジストリ キーをインストールします。  
  
     別のコンポーネントを使用する場合は、ファイルおよびレジストリ エントリはアンインストール 1 つのバージョン管理 VSPackage がアンインストールされますが、別の VSPackage がまだインストールされている場合。  
  
-   同じコンポーネントのバージョン管理と共有の項目を混在させないでください。  
  
     そうと、グローバルな場所と分離された場所にバージョン管理された項目を共有項目をインストールできなくなります。  
  
-   バージョン管理されたファイルをポイントする共有のレジストリ キーはありません。  
  
     この場合、別のバージョン管理 VSPackage のインストール時に共有キーが上書きされます。 2 番目のバージョンを削除した後、キーが指しているが、ファイルはなくなりました。  
  
## <a name="see-also"></a>関連項目  
 [共有およびバージョン管理 Vspackage を選択します。](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [VSPackage のセットアップ シナリオ](../../extensibility/internals/vspackage-setup-scenarios.md)