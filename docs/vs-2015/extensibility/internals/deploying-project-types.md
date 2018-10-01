---
title: プロジェクトの種類の展開 |Microsoft Docs
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
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 66069ac71fbe59e8b63126d66d2a0cc63ed095bc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537788"
---
# <a name="deploying-project-types"></a>プロジェクト タイプの配置
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[展開プロジェクトの種類](https://docs.microsoft.com/visualstudio/extensibility/internals/deploying-project-types)します。  
  
[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] 新しいプロジェクトの種類アグリゲーター (ProjectAggregator2.dll) とも再配布 (ProjectAggregator2.msi) 用の Windows インストーラー パッケージをインストールします。 マネージ コード プロジェクトの種類の新しいアグリゲーターを使用する必要があります。 ProjectAggregator2 で策の制限の動作、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]マネージ コード プロジェクトの種類が正しく動作するを防ぐアグリゲーターのプロジェクトします。 次の手順では、新しいアグリゲーターを使用するように VSPackage を変更する方法について説明します。  
  
1.  NativeHierarchyWrapper プロジェクトをソリューションから削除します。  
  
2.  セットアップから NativeHierarchyWrapper バイナリを削除します。  
  
3.  セットアップに ProjectAggregator2.msi を追加します。

