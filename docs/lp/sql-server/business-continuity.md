---
layout: HubPage
hide_bc: true
title: Документация Microsoft Azure
description: Сведения о создании и администрировании полнофункциональных приложений с использованием облачных служб Microsoft Azure. Получение документации, примеров кода, руководств и многого другого.
ms.topic: hub-page
featureFlags:
- clicktale
ms.openlocfilehash: 673c50c9c37a8dbe061e9695b8529e720b94217d
ms.sourcegitcommit: 615f8b5063aed679495d92a04ffbe00451d34a11
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48797850"
---
<div id="main" class="v2">
    <div class="container">
        <ul class="cardsY panelContent featuredContent">
            <li>
                <a href="https://www.microsoft.com/sql-server/sql-server-downloads">
                    <div class="cardSize">
                        <div class="cardPadding">
                            <div class="card">
                                <div class="cardImageOuter">
                                    <div class="cardImage">
                                        <img src="media/index/download-sql-server.svg" alt="" />
                                    </div>
                                </div>
                                <div class="cardText">
                                    <span class="likeAnH3">Загрузить SQL Server</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </a>
            </li>
            <li>
                <a href="https://azure.microsoft.com/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm">
                    <div class="cardSize">
                        <div class="cardPadding">
                            <div class="card">
                                <div class="cardImageOuter">
                                    <div class="cardImage">
                                        <img src="media/index/get-azure-sql-vm.svg" alt="" />
                                    </div>
                                </div>
                                <div class="cardText">
                                    <span class="likeAnH3">Получить виртуальную машину с SQL Server</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </a>
            </li>
            <li>
                <a href="/sql/ssms/download-sql-server-management-studio-ssms">
                    <div class="cardSize">
                        <div class="cardPadding">
                            <div class="card">
                                <div class="cardImageOuter">
                                    <div class="cardImage">
                                        <img src="media/index/download-ssms.svg" alt="" />
                                    </div>
                                </div>
                                <div class="cardText">
                                    <span class="likeAnH3">Загрузить SQL Server Management Studio</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </a>
            </li>              
        </ul>
    </div>
    <div class="container">
        <h1>Непрерывность бизнес-процессов</h1>
        <ul class="pivots tabLess">
            <li class="pivotItem" style="display: list-item;" data-id="#products">
                <a href="#products" data-linktype="self-bookmark"></a>
                <ul id="products">
                    <li class="panelItem" data-index="0">
                        <a class="singlePanelNavItem selected" href="#products1" data-linktype="self-bookmark"></a>
                        <ul class="cardsD panelContent singlePanelContent" id="products1" style="margin-top: 0px; display: flex;">
                            <li>
                                <a href="/sql/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server/">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/business-continuity/availability-groups.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>Группы доступности AlwaysOn</h3>
                                                    <p>Высокая доступность на уровне базы данных. В независимых экземплярах размещены базы данных, которые являются репликами друг друга. Эти экземпляры размещены в отказоустойчивых кластерах и позволяют разгружать запросы только для чтения к вторичным репликам.</p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li>
                            <li>
                                <a href="/sql/sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server/">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/business-continuity/failover-cluster.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>Экземпляры отказоустойчивого кластера AlwaysOn</h3>
                                                    <p>Высокая доступность на уровне экземпляра. Один экземпляр расположен между двумя или несколькими отказоустойчивыми кластерами Windows.</p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li>
                            <li>
                                <a href="/sql/database-engine/database-mirroring/database-mirroring-sql-server">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/business-continuity/db-mirroring.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>Зеркальное отображение базы данных</h3>
                                                    <p>Высокая доступность на уровне базы данных. Позволяет использовать отработку отказа, не требует отказоустойчивого кластера и предоставляет возможность создания отчетов с использованием моментальных снимков базы данных.</p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li>
                            <li>
                                <a href="/sql/database-engine/log-shipping/">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/business-continuity/log-shipping.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>доставка журналов;</h3>
                                                    <p>Функция, которая автоматически отправляет резервные копии журналов транзакций на дополнительный резервный сервер. </p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li>
                            <li>
                                <a href="/sql/relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases/">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/business-continuity/backup-restore.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>Резервное копирование и восстановление</h3>
                                                    <p>Компонент, который обеспечивает необходимую защиту важных данных, хранимых в SQL Server.</p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li>
                            <li>
                                <a href="/sql/relational-databases/logs/the-transaction-log-sql-server/">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/business-continuity/t-log-mgmt.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>Управление журналом транзакций</h3>
                                                    <p>Концепция, позволяющая упростить восстановление данных в случае аварии.</p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li>
                        </ul>
                    </li>
                </ul>
            </li>
        </ul>
    </div>
<div class="container centered pageFooter">
        <h2>Оставайтесь с нами</h2>
        <ul class="links">
           <li>
                <a href="http://aka.ms/editsqldocs" data-linktype="external">Принять участие в разработке документации по SQL</a>
            </li>
           <li>
                <a href="http://aka.ms/sqldocsurvey" data-linktype="external">Оставить отзыв о документации SQL</a>
            </li>
           <li>
                <a href="https://cloudblogs.microsoft.com/sqlserver/" data-linktype="external">Блог</a>
            </li>
            <li>
                <a href="https://twitter.com/sqldocs" data-linktype="external">Twitter</a>
            </li>
            <li>
                <a href="https://social.msdn.microsoft.com/Forums/en-US/home?forum=sqldatabaseengine&filter=alltypes&sort=lastpostdesc" data-linktype="external">Форум MSDN</a>
            </li>
            <li>
                <a href="https://feedback.azure.com/forums/908035-sql-server" data-linktype="external">Отзывы пользователей</a>
            </li>
        </ul>
    </div>