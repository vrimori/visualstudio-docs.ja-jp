---
title: コンポーネントの管理 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 2798d820249f0a1c4310569d22d8510710ca13ee
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129537"
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
  
## <a name="see-also"></a>関連項目  
 [共有とバージョン管理された Vspackage の使い分け](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [VSPackage のセットアップ シナリオ](../../extensibility/internals/vspackage-setup-scenarios.md)