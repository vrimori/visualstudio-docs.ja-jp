---
title: テスト領域 8:プラグインの切り替え |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7e62885b117e8b5fe42b1078c6fb8fbb4b68bf03
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53986233"
---
# <a name="test-area-8-plug-in-switching"></a>テスト領域 8:プラグインの切り替え
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) では、ユーザー インターフェイス (UI) を持つ現在のソース管理プラグインを変更します。 このテストの領域は、ソリューションのソース管理を使用するプラグインの選択のプロセスのテスト_ケースを提供します。  

## <a name="command-menu-access"></a>コマンド メニューへのアクセス  
 次[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境のメニューのパスは、テスト_ケースで使用されます。  

-   現在ソース管理プラグイン:**ツール** -> **オプション** -> **ソース管理** -> **プラグインの選択**します。  

-   ソースの変更管理のバインディング。**ファイル** -> **ソース管理** -> **ソース管理の変更**.  

## <a name="common-expected-behavior"></a>共通の想定される動作  
 ソース管理ソリューションのプラグインの変更は、Visual Studio を終了するか、またはソリューションを再読み込みせず可能性があります。 さらに、現在のソース管理プラグインは、そのソリューションが読み込まれるときに、ソリューションで使用される 1 つに自動的に変更します。  

## <a name="test-cases"></a>テスト ケース  
 プラグインの切り替えテスト区分の特定のテスト_ケースを次に示します。  

### <a name="case-8a-automatic-change"></a>大文字と小文字の 8 a:自動の変更  

#### <a name="expected-behavior"></a>想定される動作  
 ユーザーには、ソース管理下にあるソリューションが読み込まれたら、ソリューションが自動的に読み込まれ、適切なソース管理プラグインは、現在選択されています。  


| アクション | テスト ステップ | 予想される結果を確認します |
| - | - | - |
| 自動のソース管理プラグインの変更 | 1.現在テスト プラグインの選択 (**ツール** -> **オプション** -> **ソース管理** -> **プラグイン選択**)。<br />2.新しいプロジェクトを作成します。<br />3.ソース管理にソリューションを追加します。<br />4.別のプラグインを選択します (たとえば、 [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)])。<br />5.ソリューションのアンロードのプロンプトを受け入れます。<br />6.ディスクからソリューションを再度開きます。 | ソリューションが開かれます。<br /><br /> テスト対象プラグインは、現在のソース管理プラグインです。 |

### <a name="case-8b-solution-based-change"></a>大文字と小文字の 8 b:ソリューションに基づく変更  

#### <a name="expected-behavior"></a>想定される動作  
 ソリューションは、その関連ソース管理プラグインを変更できます。  


| アクション | テスト ステップ | 予想される結果を確認します |
|----------------------------------| - | - |
| ソリューションのプラグインの変更 | 1.現在テスト プラグインの選択 (**ツール** -> **オプション** -> **ソース管理** -> **プラグイン選択**)。<br />2.新しいプロジェクトとソリューションを作成します。<br />3.ソース管理にソリューションを追加します。<br />4.ソース管理からソリューションのバインドを解除 (を使用して、**ソース管理の変更** ダイアログ ボックス)。<br />5.別のプラグインを選択します (たとえば、 [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)])。<br />6.アンロードされた場合は、ディスクからソリューションを再読み込みします。<br />7.ソース管理にソリューションを追加します。<br />8.ソース管理からソリューションのバインドを解除 (を使用して**ソース管理の変更** ダイアログ ボックス)。<br />9.もう一度テスト プラグインを選択します。<br />10.アンロードされた場合は、ディスクからソリューションを再読み込みします。<br />11.元の場所に、ソリューションをバインド (を使用して、**ソース管理の変更** ダイアログ ボックス)。 | ソリューションは、選択したを使用してソース管理に追加プラグイン。 |

## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン向けのテスト ガイド](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)