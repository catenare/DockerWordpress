# Task definitions stored at AWS
## Existing config
* `aws ecs list-task-definitions --profile nziswano`
* Response:
```json
{
    "taskDefinitionArns": [
        "arn:aws:ecs:us-east-1:338196870821:task-definition/wordpress_fargate:8"
    ]
}
```
* `aws ecs describe-task-definition --task-definition wordpress_fargate:8 --profile nziswano`
* Response:
```json
{
    "taskDefinition": {
        "taskDefinitionArn": "arn:aws:ecs:us-east-1:338196870821:task-definition/wordpress_fargate:8",
        "containerDefinitions": [
            {
                "name": "nginx",
                "image": "338196870821.dkr.ecr.us-east-1.amazonaws.com/nziswano-nginx:e99dfb62c0e139f7f8d70c95bf9a3037de04e4d4",
                "cpu": 0,
                "links": [],
                "portMappings": [
                    {
                        "containerPort": 80,
                        "hostPort": 80,
                        "protocol": "tcp"
                    }
                ],
                "essential": false,
                "entryPoint": [],
                "command": [],
                "environment": [],
                "mountPoints": [
                    {
                        "sourceVolume": "wordpress",
                        "containerPath": "/var/www/html",
                        "readOnly": true
                    }
                ],
                "volumesFrom": [],
                "linuxParameters": {
                    "capabilities": {}
                },
                "privileged": false,
                "readonlyRootFilesystem": false,
                "dnsServers": [],
                "dnsSearchDomains": [],
                "dockerSecurityOptions": [],
                "pseudoTerminal": false,
                "logConfiguration": {
                    "logDriver": "awslogs",
                    "options": {
                        "awslogs-group": "/ecs/wordpress_fargate",
                        "awslogs-region": "us-east-1",
                        "awslogs-stream-prefix": "ecs"
                    }
                }
            },
            {
                "name": "wordpress",
                "image": "338196870821.dkr.ecr.us-east-1.amazonaws.com/nziswano-wordpress:7eb0611df2194cc234bdf567aa3e5ec9b3d42c47",
                "cpu": 0,
                "links": [],
                "portMappings": [],
                "essential": true,
                "entryPoint": [],
                "command": [],
                "environment": [
                    {
                        "name": "AUTH_SALT",
                        "value": "22b938073218c4d8f0f10a3d36d352b8"
                    },
                    {
                        "name": "WORDPRESS_DB_USER",
                        "value": "admin"
                    },
                    {
                        "name": "WORDPRESS_DB_HOST",
                        "value": "paseo-wordpress.cluster-cekadktwh2r8.us-east-1.rds.amazonaws.com"
                    },
                    {
                        "name": "WORDPRESS_DB_NAME",
                        "value": "wordpress"
                    },
                    {
                        "name": "NONCE_KEY",
                        "value": "cb584e44c43ed6bd0bc2d9c7e242837d"
                    },
                    {
                        "name": "SECURE_AUTH_KEY",
                        "value": "a8ee42c175b2b516d1f81ff992db030b"
                    },
                    {
                        "name": "AUTH_KEY",
                        "value": "c3def60d6b870cb9ddfd5a37e5cc4cb2"
                    },
                    {
                        "name": "SECURE_AUTH_SALT",
                        "value": "4e3baa46296d1358ea19f237ee1a5d19"
                    },
                    {
                        "name": "WORDPRESS_DB_PASSWORD",
                        "value": "r4qHXRtqKy8qU"
                    },
                    {
                        "name": "LOGGED_IN_SALT",
                        "value": "1321b53ca4bc07e4d53fa198e59af3e7"
                    },
                    {
                        "name": "MY_KEY",
                        "value": "5931acc50be4d738a0f530dc4709d155"
                    },
                    {
                        "name": "LOGGED_IN_KEY",
                        "value": "bcedc450f8481e89b1445069acdc3dd9"
                    },
                    {
                        "name": "NONCE_SALT",
                        "value": "283a64ff44db59568cc77dba8196046b"
                    },
                    {
                        "name": "WP_DEBUG",
                        "value": "true"
                    }
                ],
                "mountPoints": [
                    {
                        "sourceVolume": "wordpress",
                        "containerPath": "/var/www/html",
                        "readOnly": false
                    }
                ],
                "volumesFrom": [],
                "linuxParameters": {
                    "capabilities": {}
                },
                "privileged": false,
                "readonlyRootFilesystem": false,
                "dnsServers": [],
                "dnsSearchDomains": [],
                "dockerSecurityOptions": [],
                "pseudoTerminal": false,
                "logConfiguration": {
                    "logDriver": "awslogs",
                    "options": {
                        "awslogs-group": "/ecs/wordpress_fargate",
                        "awslogs-region": "us-east-1",
                        "awslogs-stream-prefix": "ecs"
                    }
                }
            }
        ],
        "family": "wordpress_fargate",
        "executionRoleArn": "arn:aws:iam::338196870821:role/ecsTaskExecutionRole",
        "networkMode": "awsvpc",
        "revision": 8,
        "volumes": [
            {
                "name": "wordpress",
                "host": {}
            }
        ],
        "status": "ACTIVE",
        "requiresAttributes": [
            {
                "name": "com.amazonaws.ecs.capability.logging-driver.awslogs"
            },
            {
                "name": "ecs.capability.execution-role-awslogs"
            },
            {
                "name": "com.amazonaws.ecs.capability.ecr-auth"
            },
            {
                "name": "com.amazonaws.ecs.capability.docker-remote-api.1.19"
            },
            {
                "name": "com.amazonaws.ecs.capability.docker-remote-api.1.17"
            },
            {
                "name": "ecs.capability.execution-role-ecr-pull"
            },
            {
                "name": "com.amazonaws.ecs.capability.docker-remote-api.1.18"
            },
            {
                "name": "ecs.capability.task-eni"
            }
        ],
        "placementConstraints": [],
        "compatibilities": [
            "EC2",
            "FARGATE"
        ],
        "requiresCompatibilities": [
            "FARGATE"
        ],
        "cpu": "512",
        "memory": "1024"
    }
}

```