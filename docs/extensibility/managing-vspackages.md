---
title: Vspackage の管理 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 14aa17f4692857d650cb3bc9fe1a3498fc4f147a
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639564"
---
# <a name="manage-vspackages"></a>Vspackage を管理します。
ほとんどの場合は、プロジェクトと項目テンプレートの登録し、パッケージを自動的に読み込むため、Vspackage の管理について心配する必要はありません。 ただし、状況によっては、パッケージを管理するためにさらに詳しくを学習する必要があります。  
  
## <a name="use-the-experimental-instance"></a>実験用インスタンスを使用して、  
 実験用インスタンスの詳細についてを参照してください。[実験用インスタンス](../extensibility/the-experimental-instance.md)します。  
  
## <a name="register-and-unregister-vspackages"></a>登録して、Vspackage の登録解除  
 登録し、Vspackage とその他の種類の拡張機能の登録を解除する方法については、次を参照してください。[登録し、Vspackage の登録解除](../extensibility/registering-and-unregistering-vspackages.md)します。  
  
## <a name="load-a-vspackage"></a>VSPackage を読み込む  
 Vspackage は、autoload 特定 CMDUICONTEXT GUID の電源がオンに設定できます。 詳細については、次を参照してください。[ロード Vspackage](../extensibility/loading-vspackages.md)します。  
  
## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>AsyncPackage を使用して、バック グラウンドで Vspackage を読み込む  
 `AsyncPackage`クラスは、Visual Studio での UI の応答性の向上のバック グラウンド スレッドでのパッケージの読み込みを使用できます。 詳細については、次を参照してください。[方法: バック グラウンドで Vspackage を読み込む使用 AsyncPackage](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)。  
  
## <a name="rule-based-ui-context-for-extensions"></a>ルール ベースの UI コンテキストの拡張機能  
 ルール ベースの UI コンテキストを使用する UI コンテキストがアクティブになるし、関連付けられている Vspackage が読み込まれる正確な条件を定義する拡張機能の作成者。 詳細については、次を参照してください。[方法: Visual Studio 拡張機能のルール ベースの UI コンテキストを使用して](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md)します。  
  
## <a name="diagnose-extension-performance"></a>拡張機能のパフォーマンスを診断する  
拡張機能は、起動とソリューションの読み込みのパフォーマンスに影響します。 Visual Studio 拡張機能への影響を計算する方法およびどのできます分析することがローカルで拡張機能を拡張機能に影響を与えるパフォーマンスとして表示することがあるかどうかを説明します。 詳細については、次を参照してください。[方法: 拡張機能のパフォーマンス診断](how-to-diagnose-extension-performance.md)します。 
  
## <a name="troubleshoot-vspackages"></a>Vspackage をトラブルシューティングします。  
 読み込まれないか、エラーが発生する Vspackage のトラブルシューティングの手法を調べる: [Vspackage のトラブルシューティング](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>関連項目  
 [VSPackage](../extensibility/internals/vspackages.md)