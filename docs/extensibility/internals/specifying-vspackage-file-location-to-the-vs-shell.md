---
title: VS Shell VSPackage ファイルの場所を指定する |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 88cde80499cc56adc2b347b45a4776257ec0e040
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53988311"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>VSPackage ファイルの場所を VS Shell に指定する
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] アセンブリを VSPackage を読み込む DLL を検索できる必要があります。 次の表に示すよう、さまざまな方法でこれを検索できます。  


| メソッド | 説明 |
| - | - |
| コードベースのレジストリ キーを使用します。 | コードベースのキーを使用するように指示[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]を任意の完全修飾ファイル パスから、VSPackage アセンブリを読み込めません。 キーの値は、DLL にファイル パスを指定する必要があります。 これが最善の方法は、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]パッケージ アセンブリを読み込みます。 この手法は、「コードベース/プライベート インストール ディレクトリ方法」と呼ばれることがあります。 登録時に、コードベースの値は登録する属性クラスのインスタンスを通じて、<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext>型。 |
| DLL を配置、 **PrivateAssemblies**ディレクトリ。 | 内のアセンブリを配置、 **PrivateAssemblies**のサブディレクトリ、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ディレクトリ。 アセンブリに配置**PrivateAssemblies**が自動的に検出されたに表示されない、**参照の追加** ダイアログ ボックス。 間の差**PrivateAssemblies**と**PublicAssemblies**はアセンブリで**PublicAssemblies**で列挙、**参照の追加**  ダイアログ ボックス。 "コードベース/プライベート installation directory"の手法を使用しないように選択したかどうかをインストールする必要があります、 **PrivateAssemblies**ディレクトリ。 |
| 厳密な名前のアセンブリとアセンブリのレジストリ キーを使用します。 | アセンブリ キーを使用するにはように明示的に指示[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]という名前の VSPackage アセンブリを読み込む、強力な。 アセンブリの厳密な名前キーの値があります。 |
| DLL を配置、 **PublicAssemblies**ディレクトリ。 | 最後に、アセンブリもに配置できる、 **PublicAssemblies**サブディレクトリ。 アセンブリに配置**PublicAssemblies**は自動的に検出し、も表示されます、**参照の追加** ダイアログ ボックスで[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。<br /><br /> VSPackage アセンブリにのみ配置する必要があります、 **PublicAssemblies**ディレクトリが含まれている場合は他の VSPackage 開発者が再利用を想定しているコンポーネントを管理します。 アセンブリの大半は、この条件を満たしていません。 |

> [!NOTE]
>  すべての依存アセンブリの厳密な名前の符号付きのアセンブリを使用します。 これらのアセンブリは、独自のディレクトリまたはグローバル アセンブリ キャッシュ (GAC) にもインストールする必要があります。 これを弱い名前のバインドと呼ばれる、同じ基本ファイル名を持つアセンブリとの競合を防ぎます。