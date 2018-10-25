---
title: DslTextTransform コマンド |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, commands
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 882d2c8d0dec5e4673b24436067bd6255c2052be
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853156"
---
# <a name="the-dsltexttransform-command"></a>DslTextTransform コマンド
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DslTextTransform.cmd、TextTransform.exe を呼び出すし、一般的なオプションを使用して実行するスクリプトです。 DslTextTransformation.cmd を使用して、夜間のビルドを自動化することができます、[!INCLUDE[dsl](../includes/dsl-md.md)]プロジェクト。 詳細については、次を参照してください。 [TextTransform ユーティリティを使ってファイルを生成する](../modeling/generating-files-with-the-texttransform-utility.md)します。  
  
 DslTextTransform.cmd については、次のディレクトリにあります。  
  
 **\<Visual Studio SDK Installation Path>\VisualStudioIntegration\Tools\Bin**  
  
 DslTextTransform.cmd への入力として、次の引数を指定できます。  
  
- ドメイン モデル プロジェクトの出力ディレクトリ。  
  
- デザイナー定義プロジェクトの出力ディレクトリ。  
  
- テキスト テンプレート ファイルの場所。  
  
  DslTextTransform.cmd では、既定のディレクティブ プロセッサとアセンブリを使用して、指定したテキスト テンプレート ファイルを処理します。 カスタム ディレクティブ プロセッサを作成する場合は、独自 TextTransform.exe を呼び出すバッチ ファイルを作成できます。 このバッチ ファイルでは、アセンブリと関連付けられているカスタム ディレクティブ プロセッサを指定できます。



